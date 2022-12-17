Serialization anomaly, also known as serialization failure, occurs when two or more transactions are executed concurrently and their interleaved execution produces an inconsistent result. This can happen when the transactions modify the same data in a way that conflicts with each other.

For example, consider two transactions `T1` and `T2` that each update a row in a table. If `T1` reads the row, updates it, and then `T2` reads the same row, updates it, and then `T1` updates it again, the final value of the row will depend on the order in which the transactions were executed. This can result in an inconsistent state of the data, known as a serialization anomaly.

There are two rows in the database. One has the value "**white**" and the other "**black**". Transaction 1 updates all white to black, Transaction 2 all black to white.

**Transaction 1**: 
```SQL
UPDATE table SET value = 'black' WHERE value = 'white'
```

**Transaction 2**:
```SQL
UPDATE table SET value = 'white' WHERE value = 'black'
```

### Code Example

```ruby
class User < ActiveRecord::Base
  def self.transfer_funds(from_id, to_id, amount)
    # Start a transaction, set the isolation level to "read committed"
    ActiveRecord::Base.transaction(isolation: :read_committed) do
      # Read the balances of the two accounts
      from_user = User.find(from_id)
      to_user = User.find(to_id)
      puts "Before transfer: #{from_user.name} has $#{from_user.balance}, #{to_user.name} has $#{to_user.balance}"

      # Transfer the funds
      from_user.balance -= amount
      to_user.balance += amount
      from_user.save!
      to_user.save!
      puts "After transfer: #{from_user.name} has $#{from_user.balance}, #{to_user.name} has $#{to_user.balance}"
    end
  end
end

```

This model defines a method `transfer_funds` that transfers a specified amount of money from one account to another. The method reads the balances of the two accounts, updates the balances, and then saves the changes to the database.

If we execute this method concurrently on two different accounts, we may see a serialization anomaly. For example:

```ruby
# Start a new thread to transfer funds from account 1 to account 2
Thread.new do
  User.transfer_funds(1, 2, 100)
end

# Start a new thread to transfer funds from account 2 to account 1
Thread.new do
  User.transfer_funds(2, 1, 50)
end
```

In this example, the two transactions are executed concurrently, and their interleaved execution can result in an inconsistent state of the balances. For example, if `T1` reads the balance of `account1`, updates it, and then `T2` reads the balance of `account2`, updates it, and then `T1` updates the balance of `account1` again, the final balances of the accounts will depend on the order in which the transactions were executed. This can result in a serialization anomaly.

>[!INFO]
>To prevent serialization anomalies, database systems use isolation levels to control the concurrency of transactions. The highest isolation level, [[SERIALIZABLE]] ensures that transactions are executed one at a time, in the order in which they were initiated. This eliminates the possibility of serialization anomalies, but can also reduce concurrency and performance. Lower isolation levels, such as [[REPEATABLE_READ]] and [[READ_COMMITTED]], allow transactions to be executed concurrently, but can still result in serialization anomalies if they are not carefully designed.

>[!WARNING]
> [[Database Locks#^26fc88|Deadlock]] is possible in serializable level of isolation.