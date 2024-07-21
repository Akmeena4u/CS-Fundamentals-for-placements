
### Table of Contents

<!-- TOC_START -->
| No. | Questions |
| --- | --------- |
| 1 | [Explain Functional Dependency (FD) and its components](#explain-functional-dependency-fd-and-its-components) |
| 2 | [What are Armstrong's axioms and their role in defining Functional Dependencies?](#what-are-armstrongs-axioms-and-their-role-in-defining-functional-dependencies) |
| 3 | [What is Normalisation and what is the Advantages and Disadvantages in the context of database optimization?](#what-is-normalisation-and-what-is-the-advantages-and-disadvantages-in-the-context-of-database-optimization) |
| 4 | [Describe the types of anomalies that Normalisation aims to eliminate](#describe-the-types-of-anomalies-that-normalisation-aims-to-eliminate) |
| 5 | [What are the different Normal Forms (NF) and their requirements?](#what-are-the-different-normal-forms-nf-and-their-requirements) |
| 6 | [What is a Transaction in database management?](#what-is-a-transaction-in-database-management) |
| 7 | [Why are Transactions Important? Explain the ACID properties in the context of database transactions](#why-are-transactions-important-explain-the-acid-properties-in-the-context-of-database-transactions) |
| 8 | [Here's how transactions work and describe the different states of a transaction lifecycle](#heres-how-transactions-work-and-describe-the-different-states-of-a-transaction-lifecycle) |
| 9 | [What mechanisms in DBMS support atomicity and durability in transactions?](#what-mechanisms-in-dbms-support-atomicity-and-durability-in-transactions) |
| 10 | [Explain the shadow-copy scheme in the context of ensuring atomicity and durability and also show drawbacks](#explain-the-shadow-copy-scheme-in-the-context-of-ensuring-atomicity-and-durability-and-also-show-drawbacks) |
| 11 | [What is a Write-Ahead Log (WAL) based recovery in DBMS?](#what-is-a-write-ahead-log-wal-based-recovery-in-dbms) |
| 12 | [Differentiate between deferred database modifications and immediate database modifications](#differentiate-between-deferred-database-modifications-and-immediate-database-modifications) |
<!-- TOC_END -->

## Normalisation

### Explain Functional Dependency (FD) and its components.**
> Functional Dependency (FD) in a relation means a relationship between attributes, where the value of one attribute determines the value of another. It consists of a determinant (left side) and a dependent (right side). For example, in A → B, A is the determinant and B is the dependent.

### What are Armstrong's axioms and their role in defining Functional Dependencies?
> - Armstrong's axioms are a set of axioms or logical statements that describe the properties of functional dependencies (FDs) in a relational database
> - These are fundamental to understanding and manipulating FDs during the process of normalization and database design.
> - **Reflexive:**  If A is a set of attributes and B is a subset of A, then A → B holds.
> - **Augmentation:** If A → B holds, then AX → BX holds for any set of attributes X.
> - **Transitivity:** If A → B and B → C, then A → C. These axioms help in deriving and validating FDs in database normalization.


### What is Normalisation and what is the Advantages and Disadvantages in the context of database optimization?
> Normalisation is a step towards DB optimization.
> It divides the composite attributes into individual attributes OR a larger table into smaller ones and links them using relationships.
> 
> **Advantages:**
> - **Minimize Redundancy:** Minimize redundancy by eliminating duplicate data storage.
> - **Avoid Update Anomalies:** Prevent insertion, update, and deletion anomalies that can lead to data inconsistency.
> - **Simplify Querying:** Well-structured normalized databases make querying more straightforward and efficient
> - **Facilitate Maintenance:** Changes to the database structure are easier to implement and less error-prone in normalized databases.
> - **Improved performance:** Improve database performance by reducing unnecessary data storage and ensuring efficient data retrieval.
>
> **Disadvantages:**
> - May result in an increased number of tables, which can lead to more complex queries and joins.
> - Over-normalization can lead to performance issues, especially in read-heavy applications, due to frequent joins.
> - Requires careful analysis and planning to ensure that the database design meets both current and future requirements without unnecessary complexity.



### Describe the types of anomalies that Normalisation aims to eliminate.
> - **1. Insertion Anomaly:** When certain data (attribute) can not be inserted into the DB without the presence of other data.
>     Example: The library adds a new book, but can't if the borrower (linked by ID) isn't registered yet. the insertion fails due to missing data, even though the book information is complete.
> - **2. Deletion Anomaly:** When the deletion of a data results in an Unintended loss of other data.
>    Example: A music app stores playlists with song IDs. Deleting a song might remove it from all playlists unintentionally.
> - **3. Updation Anomaly:** When update of a single data value requires multiple rows to be updated and due requiring updation at multiple places could arises Inconsistency if we forget to update data at all places
>   Example: An Albums table stores artist names. If the artist changes their name, you'd need to update it in every album entry.
>
> - **How Normalisation reduces these anomalies>**
> - Normalisation reduce these By separating data into multiple tables based on relationships, normalization ensures each data point is stored only once.
> - Normalization also uses foreign keys to link all tables so that Deleting a record in one table won't cascade to unintended deletions in another if the relationship is properly defined.



### What are the different Normal Forms (NF) and their requirements?
> A Normal form is a set of rules that define a specific level of data organization. These rules aim to reduce data redundancy and improve data integrity in relational databases. There are several normal forms, each building on the previous one:
> - **1NF (First Normal Form):** The most basic level. Ensures each table cell contains a single atomic value (indivisible piece of data, no multi-valued attributes ), not lists or groups of values. to implement this we Separate all multi-valued into distinct cells or new tables.
> - **2NF (Second Normal Form):** Build on 1NF and eliminates all partial dependencies. This means all non-key attributes (non-unique identifiers) must depend entirely on the full primary key (main table identifier), not just a part of it.
> - **3NF (Third Normal Form):** Builds on 2NF and removes transitive dependencies. In simpler terms, no data element should depend on another non-key attribute – it should rely solely on the primary key
> - **BCNF (Boyce-Codd Normal Form):** Every determinant (a set of attributes that determines another attribute) in the table must be a candidate key (a minimal set of attributes that uniquely identifies a row)..


---
---

## Transaction in database management

### What is a Transaction in database management?

> **Answer:** A database transaction is a logical unit of work that generally includes a series of operations like read, write, delete, and update within a DBMS.  If all operations are successful, the changes are permanently applied to the database and if one operation of the transaction fails, the whole transaction fails and all changes are rolled back, leaving the database in its original state. 

### Why are Transactions Important? Explain the ACID properties in the context of database transactions.
> Transactions provide several crucial benefits for database systems:
> **Answer:**
> - **Atomicity:** Ensures that either all operations within a transaction are successfully completed and applied to the database, or none of them are.This prevents partially completed changes, maintaining data consistency.
> - **Consistency:** Guarantees that the database remains in a consistent state before and after the transaction, adhering to all defined integrity constraints.
> - **Isolation:** Allows multiple transactions to execute concurrently without interfering with each other. Each transaction sees a consistent view of the database.
> - **Durability:** Ensures that once a transaction commits successfully, its changes are permanently stored in the database, even in the event of system failures.
>
> By encapsulating database operations within transactions, you can maintain data accuracy and avoid inconsistencies, especially in critical applications where data integrity is paramount.

### Here's how transactions work and describe the different states of a transaction lifecycle.
> THese are the multiple states of transaction from start to terminate
> - **Active state:** The initial state where the transaction is actively performing read and write operations.
> - **Partially committed state:** After execution, changes are temporarily stored in the buffer. If successful, the transaction moves to the committed state; if unsuccessful, it moves to the failed state.
> - **Committed state:** Indicates that all changes made by the transaction are successfully applied to the database. It's a final state where changes are permanent.
> - **Failed state:** Occurs when a transaction encounters an error during execution, making it impossible to continue. It transitions to the aborted state.
> - **Aborted state:** After failure, all changes are undone (rolled back), and the transaction ends in this state.
> - **Terminated state:** A transaction reaches this state after either committing or aborting, signifying its completion.
> - ![image](https://github.com/Akmeena4u/CS-Fundamentals-for-placements/assets/93425334/064336e5-3f95-48b5-bab8-bdb0317c7b11)



### What mechanisms in DBMS support atomicity and durability in transactions?
> **Answer:** The recovery mechanism component of DBMS supports atomicity and durability. It includes techniques like the shadow-copy scheme and log-based recovery methods to ensure these properties.

### Explain the shadow-copy scheme in the context of ensuring atomicity and durability and also show drawbacks.
> **Answer:** The shadow-copy scheme involves creating a complete copy of the database (shadow copy) before a transaction (T) updates the database. The transaction updates the new copy while leaving the original untouched. If the transaction fails, the new copy is deleted, ensuring atomicity. If the transaction succeeds, the db-pointer is updated to point to the new copy, ensuring durability. This way, either all updates are reflected or none, and changes are permanent once committed.
> **Drawbacks:** The primary drawback of the shadow-copy scheme is inefficiency, as it requires copying the entire database for every transaction, which can be resource-intensive and time-consuming.

### What is a Write-Ahead Log (WAL) based recovery in DBMS?
> **Answer:** Log-based recovery involves maintaining a log of each transaction in stable storage. The log records all operations performed on the database, ensuring that the database can be recovered in the event of a failure. Logs are stored before the actual transaction is applied to the database, providing a reliable method to recover and ensure atomicity and durability.

### Differentiate between deferred database modifications and immediate database modifications.
> - **Deferred Database Modifications:** All database modifications are recorded in the log, but the actual write operations are deferred until the transaction 
completes. 
> - **Immediate Database Modifications:** Database modifications are applied while the transaction is still active. 




