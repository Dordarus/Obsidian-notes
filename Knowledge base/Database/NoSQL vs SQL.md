NoSQL and SQL are two different types of database management systems ([[DMBS]]). Here are some key differences between the two:

1. **Data model**: SQL databases use a structured data model, where data is organized into tables with rows and columns. NoSQL databases, on the other hand, use a variety of data models, including document, key-value, graph, and column-family.
2. **Data manipulation**: SQL databases use structured query language (SQL) for data manipulation, which is a standard language for interacting with relational databases. NoSQL databases, on the other hand, use a variety of query languages or APIs, depending on the data model ([[NoSQL Data Models]])([[NoSQL Data Manipulation]]).
4. **Schema**: SQL databases use a fixed schema, which means that the structure of the data must be defined in advance and cannot be changed easily. NoSQL databases, on the other hand, often have a more flexible schema, which allows for more rapid development and easier handling of unstructured data.
5. **Scalability**: NoSQL databases are often designed to be horizontally scalable, which means that they can easily handle large amounts of data and high levels of concurrency by adding more machines to the system. SQL databases, on the other hand, are generally more vertically scalable, which means that they can handle larger workloads by adding more resources to a single machine.
6. **Use cases**: SQL databases are often used for traditional, structured data that needs to be queried using SQL and stored in a fixed schema. NoSQL databases, on the other hand, are often used for storing and processing large amounts of unstructured data, such as log files or social media data, and are often used in big data and web scale applications.

>[!NOTE]
>In summary, NoSQL and SQL databases are designed for different use cases and have different strengths and weaknesses. The right choice depends on the specific needs of a project.

>[!INFO] Also read
> - [[Reliability and consistency of data in NoSQL]]
> - [[ACID]]