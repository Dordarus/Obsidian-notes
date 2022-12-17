In short, a database transaction is a sequence of multiple operations performed on a database, and all served as a single logical unit of work — taking place wholly or not at all. In other words, there’s never a case that _only half of the operations_ are performed and the results saved. When a database transaction is in flight, the database state may be temporarily inconsistent, but when the transaction is committed or ends, the changes are applied.

### Why they are needed in the first place?

- System failures are inevitable, and in these cases, a transaction provides a way to ensure that the outcome is reliable and consistent. This means that the state of the database reflects all transactional changes committed before the point of failure and that transactions that were in-flight at the failure point are cleanly rolled back
- When multiple concurrent requests are hitting the database server, changing the same underlying data simultaneously, the transaction must isolate requests from each other to avoid conflicts.

![](https://images.contentful.com/po4qc9xpmpuh/6jbcyfzdVJlc6XCUbzgMzb/96b1a9f0594f1d769f2254bd1abf25c1/database-transaction-1__1_.png)

## Transaction states

During its lifecycle, a database transaction goes through multiple states. These states are called **transaction states** and are typically one of the following:

1.  **Active states:** It is the first state during the execution of a transaction. A transaction is _active_ as long as its instructions (read or write operations) are performed.
2.  **Partially committed:** A change has been executed in this state, but the database has not yet committed the change on disk. In this state, data is stored in the memory buffer, and the buffer is not yet written to disk.
3.  **Committed:** In this state, all the transaction updates are permanently stored in the database. Therefore, it is not possible to rollback the transaction after this point.
4.  **Failed:** If a transaction fails or has been aborted in the active state or partially committed state, it enters into a _failed_ state.
5.  **Terminated state:** This is the last and final transaction state after a committed or aborted state. This marks the end of the database transaction life cycle.

![](https://images.contentful.com/po4qc9xpmpuh/3CQA2Vahq9s71Iifwz8SHG/15acd162da3b04a09d5c048aa121ce8d/database-transaction-2.png)

>[!Note] Also read
>[[Database Isolation and read phenomenas]]
