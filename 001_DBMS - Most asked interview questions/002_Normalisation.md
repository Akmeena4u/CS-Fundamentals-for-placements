
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
    > - **Insertion Anomaly:** When certain data (attribute) can not be inserted into the DB without the presence of other data.
    > -  Example : Library adds a new book, but can't if the borrower (linked by ID) isn't registered yet. the insertion fails due to missing data, even though the book information is complete.
    > - **Deletion Anomaly:** When the deletion of a data results in Unintended loss of other data.
    > -  A music app stores playlists with song IDs. Deleting a song might remove it from all playlists unintentionally.
    > - **Updation Anomaly:** When update of single data value require multiple rows to be updated and due to require updation at multiple places could arises Inconsistency if we forget to update data at all places
    > - An Albums table stores artist names. If the artist changes their name, you'd need to update it in every album entry.
    > - **How Normalisation reduces these anomalies>**
    > - Normalisation reduce these By separating data into multiple tables based on relationships, normalization ensures each data point is stored only once.
    > - Normalization also uses foreign keys to link all tables so that Deleting a record in one table won't cascade to unintended deletions in another if the relationship is properly defined.

pen_spark


6. **What are the different Normal Forms (NF) and their requirements?**

    > **Answer:**
    > - **1NF (First Normal Form):** Requires all attributes to have atomic (indivisible) values and eliminates multi-valued attributes.
    > - **2NF (Second Normal Form):** Builds on 1NF and eliminates partial dependencies where non-prime attributes depend on only part of the primary key.
    > - **3NF (Third Normal Form):** Builds on 2NF and eliminates transitive dependencies where non-prime attributes depend on other non-prime attributes.
    > - **BCNF (Boyce-Codd Normal Form):** Requires that for every functional dependency A → B, A must be a super key, ensuring no dependencies on non-super key attributes.

7. **What advantages does Normalisation offer in database management?**

    > **Answer:**
    > - Reduces data redundancy, leading to storage efficiency and cost savings.
    > - Improves database organization and structure, facilitating easier maintenance and scalability.
    > - Ensures data consistency and integrity by minimizing the risk of anomalies during data manipulation operations.

These interview questions and answers provide a comprehensive understanding of Normalisation in database design, covering its principles, types, advantages, and its role in optimizing database performance and data integrity.
