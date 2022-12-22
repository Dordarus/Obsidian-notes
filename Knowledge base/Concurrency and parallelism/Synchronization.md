Synchronization is the process of coordinating the actions of multiple threads or processes to ensure that shared resources are accessed in a controlled manner. Synchronization is often necessary in concurrent programming, where multiple threads or processes may need to access shared resources simultaneously. Without synchronization, shared resources may be accessed in an uncontrolled manner, leading to race conditions and other [[Synchronization issues]].

## Thread-safety

Thread-safety refers to the ability of a piece of code, data structure, or system to function correctly in a multi-threaded environment. In other words, it means that the code or system is designed to handle concurrent access from multiple threads without introducing race conditions, deadlocks, or other synchronization issues.

A piece of code is considered thread-safe if it can be used concurrently by multiple threads without the risk of data corruption or race conditions. This typically requires that the code be protected by some form of synchronization mechanism, such as locks, mutexes, or semaphores, to ensure that only one thread can access the code at a time.

A data structure is considered thread-safe if it can be used concurrently by multiple threads without the risk of data corruption or race conditions. This typically requires that the data structure be implemented using thread-safe methods and data types, and that access to the data structure be synchronized using locks, mutexes, or semaphores.

A system is considered thread-safe if it can function correctly in a multi-threaded environment without the risk of data corruption or race conditions. This typically requires that all components of the system, including code and data structures, be designed to be thread-safe.

## Syncronization objects

A synchronization object is a special type of data structure or mechanism that is used to synchronize the actions of multiple threads or processes. Synchronization objects are often used in concurrent programming, where multiple threads or processes may need to access shared resources simultaneously. Without synchronization objects, shared resources may be accessed in an uncontrolled manner, leading to race conditions and other synchronization issues.

There are several different types of synchronization objects that are used in programming languages to protect shared resources from being accessed by multiple threads simultaneously. Some common types of synchronization objects include:

- **Mutexes**: A [[Mutex|mutex]] (short for "mutual exclusion") is a synchronization object that allows only one thread to access a shared resource at a time. When a thread acquires a mutex, it blocks other threads from accessing the resource until the mutex is released. Mutexes are often implemented using a lock or semaphore, which is a special type of variable that is used to control access to shared resources.

- **Locks**: A lock is a synchronization object that is used to protect shared resources from being accessed by multiple threads simultaneously. When a thread acquires a lock, it blocks other threads from accessing the protected resource until the lock is released. Locks are often implemented using a mutex or semaphore, which is a special type of variable that is used to control access to shared resources.

- **Semaphores**: A semaphore is a synchronization object that is used to protect shared resources from being accessed by multiple threads simultaneously. A semaphore is similar to a mutex, but it allows multiple threads to acquire the semaphore concurrently, rather than allowing only a single thread to acquire it. Semaphores are often used to control access to shared resources that are used by multiple threads.

- **Condition variables**: A condition variable is a synchronization object that is used to block a thread until a specific condition is met. Condition variables are often used in conjunction with mutexes or locks to synchronize access to shared resources.

- **Read-write locks**: A read-write lock is a synchronization object that allows multiple threads to read a shared resource concurrently, but only allows a single thread to write to the resource at a time. Read-write locks are often used to improve the performance of read-heavy applications by allowing multiple threads to access the shared resource concurrently.

- **Atomic operations**: Atomic operations are special operations that are guaranteed to be executed as a single unit, without interference from other threads. Atomic operations are often used to update shared variables in a thread-safe manner.


### Locks vs Semaphores?

Locks and semaphores are both synchronization objects that are used to protect shared resources from being accessed by multiple threads simultaneously. However, there are some key differences between the two:

-   Locks are typically binary, meaning that they can be either locked or unlocked. When a thread acquires a lock, it blocks other threads from accessing the protected resource until the lock is released. This ensures that only one thread can access the resource at a time.

-   Semaphores are typically countable, meaning that they have an associated integer value that can be incremented or decremented. When a thread acquires a semaphore, it decrements the semaphore's value by one. If the value of the semaphore is already zero, the thread blocks until the semaphore is released by another thread. This allows multiple threads to acquire the semaphore concurrently, as long as the value of the semaphore is greater than zero.

>[!NOTE]
>In general, locks are simpler to use than semaphores, as they only have two states (locked or unlocked) and do not require the use of a countable value. However, semaphores are more flexible, as they can be used to control access to shared resources that are used by multiple threads concurrently.

