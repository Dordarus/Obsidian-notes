[[ACID]] (Atomicity, Consistency, Isolation, and Durability) is a set of principles that are used to ensure the reliability and consistency of data in relational databases. While NoSQL databases do not use the ACID principles, they do have their own set of principles that are designed to ensure the reliability and consistency of data. Some of the principles that are commonly used with NoSQL databases include:

1. **BASE (Basically Available, Soft state, Eventually consistent)**: BASE is a set of principles that are used to ensure the availability and consistency of data in NoSQL databases. The principles of BASE are similar to those of ACID, but they are more relaxed and allow for a higher degree of flexibility in terms of data consistency.

2. **CAP theorem (Consistency, Availability, Partition tolerance)**: The CAP theorem states that it is impossible for a distributed database to simultaneously provide all three of the following guarantees: consistency, availability, and partition tolerance. As a result, NoSQL databases must choose which of these guarantees to prioritize.

3. **Eventual consistency**: Eventual consistency is a principle that is used to ensure the consistency of data in NoSQL databases. Under this principle, data may be temporarily inconsistent, but it will eventually become consistent once all updates have been propagated to all nodes in the database.

4. **Quorum-based consistency**: Quorum-based consistency is a principle that is used to ensure the consistency of data in NoSQL databases. Under this principle, a certain number of nodes in the database must agree on the value of a piece of data before it can be considered consistent.


>[!NOTE]
>It's important to note that different NoSQL databases may prioritize different principles, and the principles that are used will depend on the specific requirements of the application.