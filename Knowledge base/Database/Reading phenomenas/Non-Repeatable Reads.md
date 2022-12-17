If you’ve got two consecutive reads in one transaction with a concurrent update in between, those reads are going to show different results even though they’re part of the same transaction.

An example might be two writers working on a blog. Our first user starts a transaction that reads a post’s title, writes to the post, and then reads that post’s title again. If a second user changes that post’s title in the middle of the first user’s transaction, the first user is going to see different values for the title across the two reads; or in other words, a non-repeatable read.

### Code example:

```ruby
# In the User model
class User < ApplicationRecord
  # Start a transaction
  User.transaction do
    # Read the value of the field "name" in the "users" table
    puts User.first.name  # Outputs: "Alice"

    # Start a new transaction
    User.transaction(isolation: :read_uncommitted) do
      # Update the value of the field "name" in the "users" table
      User.first.update(name: 'Bob')
    end

    # Read the value of the field "name" again
    puts User.first.name  # Outputs: "Bob"
  end
end
```

In this example, the first transaction reads the value of the "name" field in the "users" table, which is initially "Alice". The second transaction then modifies the value of the "name" field to be "Bob". When the first transaction reads the value of the "name" field again, it gets the value "Bob", which is not the same as the value it got earlier. This demonstrates a non-repeatable read, as the first transaction reads a value that has been modified by another transaction.

>[!INFO]
>To avoid non-repeatable reads, transactions must be isolated from each other, so that one transaction cannot read data that is being modified by another transaction. This can be achieved through the use of isolation levels in the database. The isolation level [[REPEATABLE_READ]] guarantees that data that has been read by a transaction will not be modified by other transactions until the original transaction is completed, which can prevent non-repeatable reads.

```ruby
# In the User model
class User < ApplicationRecord
  # Start a transaction with the isolation level set to "read committed"
  User.transaction(isolation: :repeatable_read) do
    # Read the value of the field "name" in the "users" table
    puts User.first.name  # Outputs: "Alice"

    # Start a new transaction
    User.transaction do
      # Update the value of the field "name" in the "users" table
      User.first.update(name: 'Bob')
    end

    # Read the value of the field "name" again
    puts User.first.name  # Outputs: "Alice"
  end
end

```

In this revised example, the isolation level is set to "repeatable read" for the first transaction. This means that the transaction will only be able to read data that has been committed by other transactions, and it also guarantees that data that has been read by the transaction will not be modified by other transactions until the original transaction is completed. As a result, when the first transaction reads the value of the "name" field in the "users" table, it gets the value "Alice" both times it reads the field. This prevents a non-repeatable read, as the first transaction reads the same value both times it reads the "name" field.
