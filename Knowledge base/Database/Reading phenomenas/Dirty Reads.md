If a transaction is in the middle of updating some data and hasn’t committed yet, and another transaction is allowed to _read_ that uncommitted data, that’s called a dirty read, and could lead to your app showing incorrect data that got rolled back.

### Code example: 

```ruby
# In the User model
class User < ApplicationRecord
  # Start a transaction with the isolation level set to "read uncommitted"
  User.transaction(isolation: :read_uncommitted) do
    # Read the value of the field "name" in the "users" table
    puts User.first.name  # Outputs: "Alice"

    # Start a new transaction
    User.transaction do
      # Update the value of the field "name" in the "users" table
      User.first.update(name: 'Bob')

      # Read the value of the field "name" again
      puts User.first.name  # Outputs: "Bob"

      # Roll back the second transaction
      raise ActiveRecord::Rollback
    end
  end

  # Read the value of the field "name" again
  puts User.first.name  # Outputs: "Alice"
end

```

In this revised example, the isolation level is set to "read uncommitted" for the first transaction. This means that the transaction will be able to read data that is being modified by other transactions that have not yet been committed. As a result, when the first transaction reads the value of the "name" field in the "users" table, it gets the value "Bob", which is not yet committed and may be rolled back. Eventually, the second transaction is rolled back, and the value of the "name" field is changed back to "Alice". This demonstrates a dirty read, as the first transaction reads a value that was not yet committed.

### Using [[READ_COMMITTED]] isolation level

```ruby
# In the User model
class User < ApplicationRecord
  # Start a transaction with the isolation level set to "read uncommitted"
  User.transaction(isolation: :read_committed) do
    # Read the value of the field "name" in the "users" table
    puts User.first.name  # Outputs: "Alice"

    # Start a new transaction
    User.transaction do
      # Update the value of the field "name" in the "users" table
      User.first.update(name: 'Bob')

      # Read the value of the field "name" again
      puts User.first.name  # Outputs: "Alice"

      # Roll back the second transaction
      raise ActiveRecord::Rollback
    end
  end

  # Read the value of the field "name" again
  puts User.first.name  # Outputs: "Alice"
end
```

For this time when the first transaction reads the value of the "name" field in the "users" table, it gets the value "Alice". Dirty read prevented by higher level of isolation.