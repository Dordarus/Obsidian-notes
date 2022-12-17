A distributed transaction is a type of [[Transaction|transaction]] that involves multiple nodes, each of which has a local database that it needs to update as part of the transaction. The goal of a distributed transaction is to maintain the consistency and integrity of the distributed database system, even in the case of failures or errors during the transaction.

Distributed transactions can be complex to manage, as they involve coordinating updates to multiple databases and ensuring that the updates are either all completed or all rolled back in the event of a failure. To handle this complexity, distributed database systems often use a protocol such as the [[Two-phase commit|two-phase commit]] protocol to coordinate the updates to the participating nodes.

In a distributed transaction, each node plays a specific role in the coordination of the transaction. The coordinator node initiates the transaction and coordinates the updates to the participating nodes. The participating nodes, also known as "resource managers," are responsible for updating their local databases and reporting the results back to the coordinator.

>[!INFO]
>Examples of distributed transactions include financial transactions that involve multiple bank accounts, supply chain management systems that track the movement of goods between different locations, and online reservation systems that involve multiple hotel and airline databases. In each of these cases, the distributed transaction ensures that the updates to the local databases are consistent and correct, even if errors or failures occur during the transaction.

### Nodes

A node is a participant in the transaction that has a local database that it needs to update as part of the transaction. A node may be a server, a database, or any other system that is part of the distributed database system and that needs to be updated as part of the transaction.

In a distributed transaction, each node plays a specific role in the coordination of the transaction. The coordinator node initiates the transaction and coordinates the updates to the participating nodes. The participating nodes, also known as "resource managers," are responsible for updating their local databases and reporting the results back to the coordinator.

During the course of the transaction, the coordinator may send requests to the participating nodes, asking them to prepare to commit the transaction or to roll back the transaction in the event of a failure. The participating nodes then update their local databases and send a response back to the coordinator, indicating whether they are ready to commit the transaction or not.

>[!NOTE]
>In summary, a node in the context of a distributed transaction is a participant in the transaction that is responsible for updating its local database and reporting the results back to the coordinator.