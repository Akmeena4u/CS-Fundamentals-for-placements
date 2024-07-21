
### Table of Contents

<!-- TOC_START -->
| No. | Questions |
| --- | --------- |
| 1 | [What is indexing in DBMS and why is it used?](#what-is-indexing-in-dbms-and-why-is-it-used) |
| 2 | [Types of indices or dense v/s sparse indices](#types-of-indices-or-dense-vs-sparse-indices) |
| 3 | [What is a primary index (Clustering), and how is it different from a secondary index (Non-clustering)?](#what-is-a-primary-index-clustering-and-how-is-it-different-from-a-secondary-index-non-clustering) |
| 4 | [What are the advantages and limitations of indexing in DBMS?](#what-are-the-advantages-and-limitations-of-indexing-in-dbms) |
| 5 | [Explain Step-by-Step Approach to Introduce Indexing in DBMS](#explain-step-by-step-approach-to-introduce-indexing-in-dbms) |
| 6 | [What is database clustering and why is it used?](#what-is-database-clustering-and-why-is-it-used) |
| 7 | [Describe the basic working mechanism of clustering](#describe-the-basic-working-mechanism-of-clustering) |
| 8 | [What is partitioning in DBMS and why is it used?](#what-is-partitioning-in-dbms-and-why-is-it-used) |
| 9 | [How does vertical partitioning differ from horizontal partitioning?](#how-does-vertical-partitioning-differ-from-horizontal-partitioning) |
| 10 | [What are the advantages of partitioning a database?](#what-are-the-advantages-of-partitioning-a-database) |
| 11 | [What is a distributed database and how is it related to partitioning?](#what-is-a-distributed-database-and-how-is-it-related-to-partitioning) |
| 12 | [What is sharding and how does it relate to horizontal partitioning?](#what-is-sharding-and-how-does-it-relate-to-horizontal-partitioning) |
| 13 | [What are the pros and cons of sharding?](#what-are-the-pros-and-cons-of-sharding) |
<!-- TOC_END -->


## Indexing 


### What is indexing in DBMS and why is it used?
> Indexing in DBMS is a technique used to optimize the performance of a database by minimizing the number of disk accesses required when a query is processed. It is a type of data structure that allows quick location and access to data in a database table, speeding up read operations like SELECT queries and WHERE clauses.
> **Index Components:** An index consists of two main components:
> - **Search Key:** Contains a copy of the primary key, candidate key, or other key values from the table.
> - **Data Reference:** A pointer that holds the address of the disk block where the value of the corresponding key is stored.

### Types of indices or dense v/s sparse indices.
> - **Dense Index:** Contains an index record for every search key value in the data file. Each index record includes the search-key value and a pointer to the first data record with that search-key value.
> - **Sparse Index:** Contains index records for only some of the search-key values. A range of index columns stores the same data block address, which reduces the number of index records and storage requirements.

### What is a primary index(Clustering), and how is it different from a secondary index(Non-clustering)?
> - **Primary Index:** Applied to a sequentially ordered data file. The search key in a primary index defines the sequential order of the file. It can be based on either primary key or non-key attributes.
> - **Types of primary indexing:** Primary indexing can be based on:
> - **Key Attribute:** The data file is sorted with respect to the primary key attribute. This forms a sparse index with the number of entries in the index file equal to the number of blocks in the data file.
> - **Non-Key Attribute:** The data file is sorted with respect to a non-key attribute. This forms a dense index with entries for all unique non-key attribute values in the data file.
>   
> - **Secondary Index:** Applied to a data file that is not sequentially ordered. It can be based on key or non-key attributes and is called secondary because another indexing method is usually already applied. It typically forms a dense index with an index record for every record in the data file.


### What are the advantages and limitations of indexing in DBMS?
> **Advantages:** 
> - Faster access and retrieval of data.
> - Reduced I/O operations during search queries.
> - **limitations:** 
> - Requires additional storage space to maintain the index table.
> - Can decrease performance for INSERT, DELETE, and UPDATE operations due to the overhead of updating the index.

### Explain Step-by-Step Approach to Introduce Indexing in DBMS
>
> 1. **Identify the Need:**
>    - Analyze frequently used queries with high disk I/O and long execution times.
>
> 2. **Choose the Index Type:**
>    - **Primary Index:** For primary key columns.
>    - **Secondary Index:** For non-primary key columns used in WHERE clauses.
>    - **Composite Index:** For queries filtering on multiple columns.
>
> 3. **Create the Index:**
>    - Single-Column Index:
>      ```sql
>      CREATE INDEX index_name ON table_name(column_name);
>      ```
>    - Multi-Column (Composite) Index:
>      ```sql
>      CREATE INDEX index_name ON table_name(column1, column2);
>      ```
>
> 4. **Monitor Performance:**
>    - Use EXPLAIN to check query plans before and after indexing.
>    - Compare execution times.
>
> 5. **Maintain the Index:**
>    - Ensure indexes are updated with data changes.
>    - Periodically rebuild indexes:
>      ```sql
>      REBUILD INDEX index_name;
>      ```
>
> 6. **Evaluate Trade-offs:**
>    - Consider additional storage and impact on write operations.
>
> 7. **Optimize:**
>    - Drop unused indexes:
>      ```sql
>      DROP INDEX index_name;
>      ```

---

## Clustering in DBMS

### What is database clustering and why is it used?
> Database clustering, also known as making replica-sets, is the process of combining multiple servers or instances to connect to a single database. It is used when one server is not sufficient to handle the volume of data or number of requests. Clustering ensures high availability, load balancing, and data redundancy by replicating the same dataset on different servers.
> 
> **Advantages:** The main advantages of database clustering include:
> - **Data Redundancy:** Ensures that data is available on multiple servers, preventing data loss in case of server failure.
> - **Load Balancing:** Distributes the workload among different servers, allowing support for more users and handling traffic spikes effectively.
> - **High Availability:** Ensures that the database remains available even if one of the servers fails, providing uninterrupted access to the data.
>
> **Disadvantages:** Some challenges of implementing clustering in DBMS include:
> - **Complexity:** Setting up and managing a clustered environment can be complex and requires careful planning and configuration.
> - **Cost:** Additional hardware and software resources are needed for clustering, which can increase costs.
> - **Synchronization:** Ensuring that data remains consistent across all nodes in the cluster can be challenging, especially in high-transaction environments.
> - **Maintenance:** Regular monitoring and maintenance are required to ensure that all nodes are functioning correctly and efficiently.


### Describe the basic working mechanism of clustering.
> In clustering architecture, user requests are distributed across multiple computers. Each request is executed and processed by various computer systems within the cluster. The system ensures load balancing and high availability by redistributing the workload if one node fails. This setup minimizes the chances of complete system failure, providing reliable and efficient database access.


---

## Partitioning & Sharding in DBMS

### What is partitioning in DBMS and why is it used?
> - Partitioning is the technique used to divide stored database objects into separate servers. Due to this, there is an increase in performance,
and controllability of the data. We can manage huge chunks of data optimally.
> - When we horizontally scale our machines/servers, we know that it gives us a challenging time dealing with relational databases as it’s quite tough to maintain the relations. But if we apply partitioning to the database that is already scaled out i.e. equipped with multiple servers, we can partition our database among those servers and handle the big data easily.

### How does vertical partitioning differ from horizontal partitioning?
> - **Vertical Partitioning:** This involves slicing the database column-wise, meaning different columns of a table are stored in separate partitions. Accessing complete tuples requires querying different servers.
> - **Horizontal Partitioning:** This involves slicing the database row-wise, where independent rows of data tuples are stored in different servers. Each server can independently handle its own chunk of data without needing to access other servers for complete tuples.


### What are the advantages of partitioning a database?
> **Advantages:** The advantages of partitioning a database include:
> - **Parallelism:** Allows multiple queries to run simultaneously on different partitions.
> - **Availability:** Increases data availability as partitions can be managed independently.
> - **Performance:** Enhances performance by reducing the amount of data each query needs to process.
> - **Manageability:** Makes it easier to manage large datasets.
> - **Cost Reduction:** Reduces costs associated with vertical scaling, as partitioning optimizes the use of existing resources.

### What is a distributed database and how is it related to partitioning?
> A distributed database is a single logical database spread across multiple locations (servers) interconnected by a network. It is a result of applying database optimization techniques such as clustering, partitioning, and sharding. This setup helps manage large datasets efficiently by distributing the data across multiple servers.

### What is sharding and how does it relate to horizontal partitioning?
> Sharding is a technique to implement horizontal partitioning. It involves splitting data across multiple database instances and introducing a routing layer to forward requests to the appropriate instance containing the data. This approach improves scalability and availability but also introduces complexity and is not well-suited for analytical queries.

### What are the pros and cons of sharding?
> - **Pros:**
>   - **Scalability:** Allows the database to handle more data and traffic by distributing it across multiple instances.
>   - **Availability:** Increases data availability as different instances can handle requests independently.
> - **Cons:**
>   - **Complexity:** Requires implementing partition mapping and a routing layer, making the system more complex.
>   - **Non-uniformity:** Creates the need for re-sharding when data distribution becomes uneven.
>   - **Not Suitable for Analytical Queries:** The data spread across different instances makes it difficult to perform analytical queries efficiently (Scatter-Gather problem).

