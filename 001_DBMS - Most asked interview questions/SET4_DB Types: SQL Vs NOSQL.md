
### Table of Contents

<!-- TOC_START -->
| No. | Questions |
| --- | --------- |
| 1 | [What is a relational database and what are its key features?](#what-is-a-relational-database-and-what-are-its-key-features) |
| 2 | [How does an object-oriented database differ from a relational database?](#how-does-an-object-oriented-database-differ-from-a-relational-database) |
| 3 | [What are the main types of NoSQL databases and their advantages?](#what-are-the-main-types-of-nosql-databases-and-their-advantages) |
| 4 | [Describe the hierarchical database model and its key advantage.](#describe-the-hierarchical-database-model-and-its-key-advantage) |
| 5 | [What are Network Databases and how do they differ from Hierarchical Databases?](#what-are-network-databases-and-how-do-they-differ-from-hierarchical-databases) |
| 6 | [What are NoSQL databases and how do they differ from relational databases?](#what-are-nosql-databases-and-how-do-they-differ-from-relational-databases) |
| 7 | [What led to the emergence of NoSQL databases, and how do they cater to modern development needs?](#what-led-to-the-emergence-of-nosql-databases-and-how-do-they-cater-to-modern-development-needs) |
| 8 | [What are some common misconceptions about NoSQL databases, and how do they differ from reality?](#what-are-some-common-misconceptions-about-nosql-databases-and-how-do-they-differ-from-reality) |
| 9 | [What are the advantages and disadvantages of using NoSQL databases compared to traditional relational databases?](#what-are-the-advantages-and-disadvantages-of-using-nosql-databases-compared-to-traditional-relational-databases) |
| 10 | [What are the advantages of using SQL (relational databases) over NoSQL databases?](#what-are-the-advantages-of-using-sql-relational-databases-over-nosql-databases) |
| 11 | [SQL vs NoSQL](#sql-vs-nosql) |
<!-- TOC_END -->

## Types of Databases

### What is a relational database and what are its key features?
> A relational database is based on the relational model and uses Structured Query Language (SQL) for operations such as creating, reading, updating, and deleting data. It stores information in discrete tables that can be joined together by fields known as foreign keys.
>  Key features include high optimization for structured data, strong data normalization guarantees, and the use of SQL for querying.
> - **Use case** Banking systems, e-commerce platforms where ACID (Atomicity, Consistency, Isolation, Durability) properties are crucial.
> - **Examples** MySQL, Microsoft SQL Server, and Oracle.

### How does an object-oriented database differ from a relational database?
> An object-oriented database is based on the object-oriented programming paradigm and treats data as objects, unlike relational databases that store data in tables.
>  Object-oriented databases support inheritance, object identity, encapsulation, and a rich type system. They can handle complex data relations and types more efficiently than relational databases.They are used in applications where data objects closely resemble real-world objects.
> - **Use case** Applications requiring complex object relationships, such as CAD/CAM systems.
> - **Examples** include ObjectDB and GemStone.
>
> - **Advantages:**
>    - Easy and quick data storage and retrieval.
>    - Can handle complex data relations and a variety of data types.
>    - Friendly for modeling advanced real-world problems.
>    - Works well with OOP and object-oriented languages.
> - **Disadvantages:**
>    - High complexity can cause performance issues like slower read, write, update, and delete operations.
>    - Less community support compared to relational databases.
>    - Does not support views like relational databases.

### What are the main types of NoSQL databases and their advantages?
> NoSQL databases are non-relational and are designed to handle unstructured or semi-structured data. They offer flexibility and scalability for large-scale distributed data environments. Types include:
> - **Document Databases:** Store data in flexible, JSON-like documents.
> - **Use case**Content management, real-time analytics, blogging platforms where flexibility in data schema is required.
> - **Examples** MongoDB, Couchbase.
>   
> - **Key-Value Stores:** Simple key-value pairs, efficient for high-speed data access.
> - **Use case** Session management, caching, real-time bidding, where fast access to large volumes of simple data structures is needed.
> - **Examples** Redis, DynamoDB.
> - 
> - **Graph Database:** Neo4j, Amazon Neptune, ArangoDB.
> - **Use case**Social networks, fraud detection, recommendation engines, where relationships between data points are as important as the data itself.

### Describe the hierarchical database model and its key advantage.
> The hierarchical database model organizes data in a tree-like structure with a root parent directory linking to subdirectory branches, where each child record can only have one parent record. The key advantage is its ease of use due to the one-to-many organization of data, making it simple and fast to traverse the database.
> This is ideal for use cases such as website drop-down menus or computer folder systems.
> - **Use case** organizing information in a company's employee structure, where individual employees report to a single department.
> - **Examples:** IBM Information Management System (IMS).


### What are Network Databases and how do they differ from Hierarchical Databases?
> Network Databases are an extension of Hierarchical Databases where child records can associate with multiple parent records, forming a graph structure. Unlike Hierarchical Databases that enforce a strict parent-child relationship, Network Databases allow more complex relationships between records.
> - **Use case**telecommunications for managing network topologies where devices may connect in various ways
> - **Example**Integrated Data Store (IDS), IDMS (Integrated Database Management System), Raima Database Manager, TurboIMAGE.


---
---

## NOSQL


### What are NoSQL databases and how do they differ from relational databases?
> NoSQL databases, also known as "not only SQL," store data differently than traditional relational databases by using flexible data models such as document, key-value, wide-column, and graph. Unlike relational databases that use a fixed schema, NoSQL databases offer schema flexibility and are optimized for scalability and performance in handling large volumes of unstructured or semi-structured data.


### What led to the emergence of NoSQL databases, and how do they cater to modern development needs?
> NoSQL databases emerged in the late 2000s as the cost of storage dramatically decreased and unstructured data increased So NoSQL databases emerged in response to the increasing complexity and scalability challenges of managing unstructured data, especially with the rise of cloud computing and agile development practices. They optimize developer productivity by allowing flexible schema design and rapid iteration without the constraints of predefined data models.


### What are some common misconceptions about NoSQL databases, and how do they differ from reality?
> There are misconceptions such as NoSQL databases not supporting ACID transactions or being unable to handle relationship data effectively. In reality, many NoSQL databases like MongoDB support ACID transactions, and they excel in managing complex relationships through specialized data models like graph databases.

### What are the advantages and disadvantages of using NoSQL databases compared to traditional relational databases?
> - **Advantages:**
>   - **Schema flexibility:** NoSQL databases do not enforce a rigid schema, allowing for easier handling of evolving data structures.
>   - **Horizontal scaling:** They support seamless distribution of data across multiple nodes, enabling efficient scalability.
>   - **High availability:** Many NoSQL databases offer built-in replication and failover mechanisms, ensuring data availability during node failures.
>   - **Performance:** Optimized data models facilitate faster reads and writes, especially beneficial for applications with large datasets and complex queries.
>
> - **Disadvantages:**
>   - **Data redundancy:** Optimized for query flexibility rather than reducing data duplication, which can lead to larger storage requirements.
>   - **Limited transaction support:** Not all NoSQL databases provide full ACID transaction capabilities, which may be essential for certain applications.
>   - **Complexity of updates and deletes:** Operations can be more complex and costly compared to relational databases, particularly in distributed environments.
>   - **Consistency challenges:** Maintaining consistency across distributed data can be more challenging due to eventual consistency models used by many NoSQL databases.


---
## SQL

### What are the advantages of using SQL (relational databases) over NoSQL databases?
> - **Advantages of SQL:**
>   - **Data Integrity:** ACID transactions ensure data consistency and integrity, crucial for mission-critical applications.
>   - **Mature Ecosystem:** SQL databases have a long-standing history, robust tooling, and strong community support.
>   - **Structured Data:** Ideal for applications with complex relationships between data entities (e.g., joins).
>   - **Scalability:** Suitable for vertical scaling scenarios where increasing server resources can handle increased load.
>
> - **Disadvantages of SQL:**
>   - **Schema Rigidity:** Changes to schemas can be complex and require downtime, impacting agility.
>   - **Scalability Limitations:** Vertical scaling may become prohibitively expensive or impractical for very large datasets or high traffic.
>   - **Performance:** Complex queries involving joins and relationships can be slower compared to NoSQL databases for certain tasks.


---

## SQL VS NOSQL



| Feature               | SQL Databases                                                   | NoSQL Databases                                                                                   |
|-----------------------|-----------------------------------------------------------------|---------------------------------------------------------------------------------------------------|
| **Data Storage Model**| Tables with fixed rows and columns                               | Document: JSON documents,<br>Key-value: key-value pairs,<br>Wide-column: tables with rows and dynamic columns,<br>Graph: nodes and edges               |
| **Development History**| Developed in the 1970s with a focus on reducing data duplication | Developed in the late 2000s with a focus on scaling and allowing for rapid application change driven by agile and DevOps practices                           |
| **Examples**          | Oracle, MySQL, Microsoft SQL Server, PostgreSQL                 | Document: MongoDB and CouchDB,<br>Key-value: Redis and DynamoDB,<br>Wide-column: Cassandra and HBase,<br>Graph: Neo4j and Amazon Neptune             |
| **Primary Purpose**   | General Purpose                                                 | Document: general purpose,<br>Key-value: large amounts of data with simple lookup queries,<br>Wide-column: large amounts of data with predictable query patterns,<br>Graph: analyzing and traversing relationships between connected data |
| **Schemas**           | Fixed                                                           | Flexible                                                                                          |
| **Scaling**           | Vertical (Scale-up)                                              | Horizontal (scale-out across commodity servers)                                                     |
| **ACID Properties**   | Supported                                                       | Not Supported, except in databases like MongoDB etc.                                                |
| **JOINS**             | Typically Required                                              | Typically not required                                                                             |
| **Data to Object Mapping** | Required object-relational mapping                             | Many do not require ORMs. MongoDB documents map directly to data structures in most popular programming languages                                            |


