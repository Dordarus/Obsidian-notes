In **relational databases**, transactions must be:
1. [[#Atomicity|Atomic]]
2. [[#Consistency|Consistent]]
3. [[#Isolation|Isolated]]
4. [[#Durability|Durable]]

These properties are commonly abbreviated as ACID. **ACID properties** ensure that a database transaction is processed reliably.

![](https://www.databricks.com/wp-content/uploads/2021/02/delta-lake-1-min.png)

## Atomicity

Atomicity in terms of a transaction means _all or nothing_. When a transaction is committed, the database either completes the transaction successfully or rolls it back so that the database returns to its original state. For example, in an online ticketing application, a booking may consist of two separate actions that form a transaction — reserving the seat for the customer and paying for the seat. A transaction guarantees that when a booking is completed, both these actions, although independent, happen within the same transaction. If any of the actions fail, the entire transaction is rolled back, and the booking is freed up for another transaction attempting to take it.

## Consistency

One of the key advantages of using a transaction is maintaining data integrity, regardless of whether it succeeds or fails. Transactions can only alter affected data in a way that is authorised by the database engine, ensuring that a consistent view of the data is maintained at all times. For example, when users deposit money in an online banking app, they want to see the result of this deposit reflected immediately when they view their balance. To ensure their money has not been lost. With strong transactional consistency, there should never appear to be more or less money in aggregate in the bank than there is.

## Isolation

With multiple concurrent transactions running at the same time, each transaction should be kept independent without affecting other transactions executing simultaneously. For most database systems, the order of the transactions is not known in advance. Transactions are instead run in parallel, and some form of database locking is utilised to ensure that the result of one transaction does not impact that of another. Typically, databases offer several **isolation levels** to control the degree of transactional integrity.

## Durability

Durability means that a successful transaction commit will survive permanently. To accomplish this, an entry is added to the database transaction log for each successful transaction.