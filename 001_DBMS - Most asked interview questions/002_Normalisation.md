
## Normalisation



1. **Explain Functional Dependency (FD) and its components.**
    > Functional Dependency (FD) in a relation means a relationship between attributes, where the value of one attribute determines the value of another. It consists of a determinant (left side) and a dependent (right side). For example, in A → B, A is the determinant and B is the dependent.

2. **What are Armstrong's axioms and their role in defining Functional Dependencies?**
    > - Armstrong's axioms are a set of axioms or logical statements that describe the properties of functional dependencies (FDs) in a relational database
    > - These are fundamental to understanding and manipulating FDs during the process of normalization and database design.
    > - **Reflexive:**  If A is a set of attributes and B is a subset of A, then A → B holds.
    > - **Augmentation:** If A → B holds, then AX → BX holds for any set of attributes X.
    > - **Transitivity:** If A → B and B → C, then A → C. These axioms help in deriving and validating FDs in database normalization.


3. **What is Normalisation and why it performed in the context of database optimization?**
    > Normalisation is a step towards DB optimisation.
    > It divides the composite attributes into individual attributes OR larger table into smaller and links them using relationships.
    > **Normalisation is performed to:**
    > - Minimize redundancy by eliminating duplicate data storage.
    > - Prevent insertion, update, and deletion anomalies that can lead to data inconsistency.
    > - Improve database performance by reducing unnecessary data storage and ensuring efficient data retrieval.
    > To perform normalisation we use normal forms
 

4. **Describe the types of anomalies that Normalisation aims to eliminate.**
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



6. **What are the different Normal Forms (NF) and their requirements?**
    > A Normal form is a set of rules that define a specific level of data organization. These rules aim to reduce data redundancy and improve data integrity in relational databases. There are several normal forms, each building on the previous one:
    > - **1NF (First Normal Form):** The most basic level. Ensures each table cell contains a single atomic value (indivisible piece of data, no multi-valued attributes ), not lists or groups of values.
    > - **2NF (Second Normal Form):** Build on 1NF and eliminates all partial dependencies. This means all non-key attributes (non-unique identifiers) must depend entirely on the full primary key (main table identifier), not just a part of it.
    > - **3NF (Third Normal Form):** Builds on 2NF and removes transitive dependencies. In simpler terms, no data element should depend on another non-key attribute – it should rely solely on the primary key
    > - **BCNF (Boyce-Codd Normal Form):** Requires that for every functional dependency A → B, A must be a super key, ensuring no dependencies on non-super key attributes.

7. **What advantages does Normalisation offer in database management?**

    > **Answer:**
    > - Reduces data redundancy, leading to storage efficiency and cost savings.
    > - Improves database organization and structure, facilitating easier maintenance and scalability.
    > - Ensures data consistency and integrity by minimizing the risk of anomalies during data manipulation operations.

These interview questions and answers provide a comprehensive understanding of Normalisation in database design, covering its principles, types, advantages, and its role in optimizing database performance and data integrity.
