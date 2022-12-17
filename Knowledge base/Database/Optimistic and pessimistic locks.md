Optimistic and pessimistic locks are two different strategies for managing concurrency and access to shared resources in a multithreaded program.

Optimistic locks, also known as optimistic concurrency control, are a strategy where threads are allowed to access and modify a shared resource without acquiring a lock, and the potential conflicts are resolved later, when the threads try to commit their changes. This allows threads to operate concurrently and independently, which can improve performance and scalability. However, it also means that conflicts are more likely to occur, and they must be handled carefully to ensure the integrity of the shared resource.

Pessimistic locks, on the other hand, are a strategy where threads are required to acquire a lock before accessing or modifying a shared resource. This prevents conflicts by ensuring that only one thread can access the resource at a time, but it can also result in lower performance and scalability, because it limits concurrency.

When deciding which type of lock to use, it is important to consider the specific needs and requirements of the program, as well as the potential trade-offs between concurrency, performance, and reliability. Optimistic locks are typically used in scenarios where conflicts are rare and can be easily resolved, while pessimistic locks are typically used in scenarios where conflicts are more common or difficult to resolve.

## In Database Systems

In database systems, locks are used to prevent multiple [[Transaction|transactions]] from accessing and modifying the same data simultaneously, which can lead to data inconsistencies. There are two main types of locks: optimistic locks and pessimistic locks.

Optimistic locks are a type of lock that allows multiple transactions to access the same data simultaneously, with the assumption that conflicts will be rare. When a transaction wants to update the data, it first checks to see if the data has been modified by another transaction since it was last accessed. If the data has not been modified, the transaction can proceed with the update. If the data has been modified, the transaction will fail and the user will need to resolve the conflict and retry the update. Optimistic locks are generally used in systems where conflicts are expected to be rare and can be resolved easily.

Pessimistic locks, on the other hand, prevent other transactions from accessing the data while a transaction is accessing it. This ensures that conflicts do not occur, but it can also lead to slower performance because other transactions have to wait for the lock to be released before they can access the data. Pessimistic locks are generally used in systems where conflicts are expected to be more common or where it is not practical to resolve conflicts.

Shared locks, exclusive locks, and intent locks are [[Database lock types|type of locks]] that can be used in conjunction with either pessimistic or optimistic concurrency control. Shared locks allow multiple transactions to read data simultaneously, but prevent any of them from updating the data until the lock is released. Exclusive locks prevent all other transactions from accessing the data until the lock is released. Intent locks are used to protect the resources that a transaction intends to access, rather than the data itself.

>[!NOTE]
>Both optimistic and pessimistic locks have their own trade-offs and are suitable for different situations. It is important to carefully consider which [[Database lock types|type of lock]] is best for a given situation in order to ensure the system performs optimally and maintains data integrity.

## Examples

### Optimistic Lock

Imagine there are two users, Alice and Bob, who are both accessing a customer database at the same time. Alice and Bob both want to update the address for the same customer, but they have different ideas about what the correct address should be.

Without any kind of lock, Alice and Bob might both try to update the address at the same time, leading to a conflict. To prevent this, the database could use an optimistic lock.

In this case, the database would allow both Alice and Bob to access the customer record at the same time, but it would keep track of the version of the record that each user accessed. When Alice or Bob tries to update the record, the database would first check to see if the record has been modified by another user since it was last accessed. If it has not been modified, the update can proceed. If the record has been modified, the update will fail and the user will need to resolve the conflict.

For example, let's say Alice starts by accessing the customer record and reading the address as "123 Main Street." She then decides to change the address to "456 Main Street" and attempts to update the record. At the same time, Bob accesses the same record and reads the address as "123 Main Street." He decides to change the address to "789 Main Street" and also attempts to update the record.

In this case, the database would detect a conflict when both Alice and Bob try to update the record. It would prompt one of them (for example, Bob) to resolve the conflict by deciding which version of the address to use. Bob could choose to use Alice's version of the address, his own version, or a completely different version. Once the conflict is resolved, the update can proceed and the record will be saved with the chosen address.

### Pessimistic Lock

Lets look how pessimistic locks might work in a database, using the same scenario as before with Alice and Bob trying to update the same customer record:

In this case, the database would use a pessimistic lock to prevent conflicts. When Alice starts by accessing the customer record and reading the address as "123 Main Street," the database would place a lock on the record to prevent other users from accessing or modifying it. This means that Bob would not be able to access the record until Alice is finished with it.

Alice decides to change the address to "456 Main Street" and updates the record. Because the lock is in place, Bob is unable to access the record until the lock is released. Once Alice is finished and the lock is released, Bob can access the record and read the updated address as "456 Main Street." Bob then decides to change the address to "789 Main Street" and updates the record.

In this case, there is no conflict because Bob was not able to access the record until the lock was released, so he was able to update the record without any issues. Pessimistic locks can prevent conflicts, but they can also lead to slower performance because other transactions have to wait for the lock to be released before they can access the data.
