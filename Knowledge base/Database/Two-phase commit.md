A two-phase commit is a protocol used to ensure that a transaction is completed in a distributed system. It involves two phases: the "prepare" phase and the "commit" phase.

In the prepare phase, the transaction manager sends a request to all participating nodes, asking them to prepare to commit the transaction. Each node then checks if it is able to commit the transaction, and responds to the transaction manager with either a "yes" or a "no" message.

If all nodes respond with a "yes" message, the transaction manager moves on to the commit phase. In the commit phase, the transaction manager sends a commit request to all participating nodes, instructing them to commit the transaction. The nodes then carry out the necessary changes and respond to the transaction manager with a "done" message to indicate that the transaction has been committed successfully.

If any node responds with a "no" message during the prepare phase, the transaction manager will abort the transaction and instruct all participating nodes to roll back any changes that were made.

An example of a two-phase commit might be a distributed database system, where multiple nodes are responsible for storing and updating data. In this case, the transaction manager would be responsible for coordinating the commit process across the nodes, to ensure that the data is updated consistently and atomically.

>[!INFO]
>Overall, the two-phase commit protocol is a useful tool for ensuring the consistency and reliability of distributed transactions, but it can be complex and time-consuming to implement, particularly in large-scale systems.

>[!INFO] Also read
>  - [[Distributed transaction]]