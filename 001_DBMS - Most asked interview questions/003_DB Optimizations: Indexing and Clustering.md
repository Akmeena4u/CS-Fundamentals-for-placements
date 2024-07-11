
## Indexing 

### Interview Questions and Answers

1. **What is indexing in DBMS and why is it used?**
    > Indexing in DBMS is a technique used to optimize the performance of a database by minimizing the number of disk accesses required when a query is processed. It is a type of data structure that allows quick location and access to data in a database table, speeding up read operations like SELECT queries and WHERE clauses.
    > **Index Components:** An index consists of two main components:
    > - **Search Key:** Contains a copy of the primary key, candidate key, or other key values from the table.
    > - **Data Reference:** A pointer that holds the address of the disk block where the value of the corresponding key is stored.

2. **Types of indices or dense v/s sparse indices.**
    > - **Dense Index:** Contains an index record for every search key value in the data file. Each index record includes the search-key value and a pointer to the first data record with that search-key value.
    > - **Sparse Index:** Contains index records for only some of the search-key values. A range of index columns stores the same data block address, which reduces the number of index records and storage requirements.

3. **What is a primary index(Clustering), and how is it different from a secondary index(Non-clustering)?**
    > - **Primary Index:** Applied to a sequentially ordered data file. The search key in a primary index defines the sequential order of the file. It can be based on either primary key or non-key attributes.
    > - **Types of primary indexing:** Primary indexing can be based on:
    > - **Key Attribute:** The data file is sorted with respect to the primary key attribute. This forms a sparse index with the number of entries in the index file equal to the number of blocks in the data file.
    > - **Non-Key Attribute:** The data file is sorted with respect to a non-key attribute. This forms a dense index with entries for all unique non-key attribute values in the data file.
    >   
    > - **Secondary Index:** Applied to a data file that is not sequentially ordered. It can be based on key or non-key attributes and is called secondary because another indexing method is usually already applied. It typically forms a dense index with an index record for every record in the data file.


4. **What are the advantages and limitations of indexing in DBMS?**
    > **Advantages:** 
    > - Faster access and retrieval of data.
    > - Reduced I/O operations during search queries.
    > **limitations:** 
    > - Requires additional storage space to maintain the index table.
    > - Can decrease performance for INSERT, DELETE, and UPDATE operations due to the overhead of updating the index.

5. **Explain Step-by-Step Approach to Introduce Indexing in DBMS**
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

## Clustering in DBMS**

1. **What is database clustering and why is it used?**
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


2. **Describe the basic working mechanism of clustering.**
> In clustering architecture, user requests are distributed across multiple computers. Each request is executed and processed by various computer systems within the cluster. The system ensures load balancing and high availability by redistributing the workload if one node fails. This setup minimizes the chances of complete system failure, providing reliable and efficient database access.




