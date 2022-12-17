If a transaction reads data and then a concurrent transaction `INSERT`s data that would have been read in the original transaction, that’s a phantom read.

### Code example:

```ruby
# In the User model
class User < ApplicationRecord
  # Start a transaction with the isolation level set to "repeatable read"
  User.transaction(isolation: :repeatable_read) do
    # Read the number of records in the "users" table
    puts User.where("name like 'A%'").count  # Outputs: 1

    # Start a new transaction
    User.transaction do
      # Create a new record in the "users" table with a name starting with "A"
      User.create(name: 'Alice')
    end

    # Read the number of records in the "users" table again, filtered by name starting with "A"
    puts User.where("name like 'A%'").count  # Outputs: 2
  end
end
```

In this example, the first transaction reads the number of records in the "users" table that have a name starting with "A", which is initially 1. The second transaction then creates a new record in the "users" table with a name starting with "A". When the first transaction reads the number of records in the table again, it gets the value 2, which includes the new record that was created by the second transaction. This demonstrates a phantom read, as the first transaction reads records that were not visible to it earlier.

>[!INFO]
>To avoid phantom reads, transactions must be isolated from each other, so that one transaction cannot see data that is being modified by another transaction. This can be achieved through the use of isolation levels in the database. The isolation level [[SERIALIZABLE]] guarantees that transactions will be executed as if they were being executed one at a time, in a serial order, which can prevent phantom reads. However, it is important to note that the "serializable" isolation level may have a significant impact on the performance of the database.

```ruby
# In the User model
class User < ApplicationRecord
  # Start a transaction with the isolation level set to "repeatable read"
  User.transaction(isolation: :serializable) do
    # Read the number of records in the "users" table
    puts User.where("name like 'A%'").count  # Outputs: 1

    # Start a new transaction
    User.transaction do
      # Create a new record in the "users" table with a name starting with "A"
      User.create(name: 'Alice')
    end

    # Read the number of records in the "users" table again, filtered by name starting with "A"
    puts User.where("name like 'A%'").count  # Outputs: 1
  end
end
```

With the isolation level set to "serializable", the second transaction will be prevented from inserting the new row until the first transaction is completed. This will prevent the phantom read from occurring.