


## DBMS Interview Questions 

### Table of Contents

<!-- TOC_START -->
| No. | Questions |
| --- | --------- |
| 1 | [Explain the key differences between data and information](#explain-the-key-differences-between-data-and-information) |
| 2 | [What is a database?](#what-is-a-database) |
| 3 | [What is a Database Management System (DBMS)?](#what-is-a-database-management-system-dbms) |
| 4 | [Why use a DBMS instead of a file-processing system?](#why-use-a-dbms-instead-of-a-file-processing-system) |
| 5 | [What is the purpose of the three-schema architecture in DBMS?](#what-is-the-purpose-of-the-three-schema-architecture-in-dbms) |
| 6 | [Describe the Three Schema Architecture of data abstraction](#describe-the-three-schema-architecture-of-data-abstraction) |
| 7 | [Differentiate between an instance and a schema in a database context](#differentiate-between-an-instance-and-a-schema-in-a-database-context) |
| 8 | [How do application programs access databases?](#how-do-application-programs-access-databases) |
| 9 | [What are the roles and responsibilities of a Database Administrator (DBA)?](#what-are-the-roles-and-responsibilities-of-a-database-administrator-dba) |
| 10 | [Describe the DBMS Application Architectures in DBMS application architectures](#describe-the-dbms-application-architectures-in-dbms-application-architectures) |
| 11 | [What is an ER Model, and what does it represent?](#what-is-an-er-model-and-what-does-it-represent) |
| 12 | [Define key terminologies of an ER Model](#define-key-terminologies-of-an-er-model) |
| 13 | [What are relationships in an ER Model? Give examples](#what-are-relationships-in-an-er-model-give-examples) |
| 14 | [What are Relationship constraints in the ER Model?](#what-are-relationship-constraints-in-the-er-model) |
| 15 | [Why do weak entities have a total participation constraint?](#why-do-weak-entities-have-a-total-participation-constraint) |
| 16 | [What is Specialisation in the context of an Extended ER Model?](#what-is-specialisation-in-the-context-of-an-extended-er-model) |
| 17 | [What is Generalisation in the Extended ER Model?](#what-is-generalisation-in-the-extended-er-model) |
| 18 | [How does Attribute Inheritance and participation inheritance work in Specialisation and Generalisation?](#how-does-attribute-inheritance-and-participation-inheritance-work-in-specialisation-and-generalisation) |
| 19 | [Explain Aggregation in the context of the Extended ER Model](#explain-aggregation-in-the-context-of-the-extended-er-model) |
| 20 | [What is ER Diagram symbols and notions?](#what-is-er-diagram-symbols-and-notions) |
| 21 | [What is the Relational Model and how does it organize data?](#what-is-the-relational-model-and-how-does-it-organize-data) |
| 22 | [What are the key properties that define a table in the Relational Model?](#what-are-the-key-properties-that-define-a-table-in-the-relational-model) |
| 23 | [What are relational keys and its types in the Relational Model?](#what-are-relational-keys-and-its-types-in-the-relational-model) |
| 24 | [Describe Integrity Constraints in the Relational Model and their significance](#describe-integrity-constraints-in-the-relational-model-and-their-significance) |
| 25 | [What are the Steps to make an ER Diagram?](#what-are-the-steps-to-make-an-er-diagram) |
| 26 | [What is the process of transforming an Entity-Relationship (ER) Model into a Relational Model?](#what-is-the-process-of-transforming-an-entity-relationship-er-model-into-a-relational-model) |
| 27 | [Explain the concept of Aggregation in the transformation from ER Model to Relational Model](#explain-the-concept-of-aggregation-in-the-transformation-from-er-model-to-relational-model) |
<!-- TOC_END -->


##   Introduction to DBMS

### Explain the key differences between data and information.

> Data is a collection of facts, while information puts those facts into context.
>Data has two types -  Quantitative data is numerical and includes measurements like weight, volume, and cost. Qualitative data is descriptive and non-numerical, including attributes like name, gender, and hair color. while info does not have types
> Data is raw and unorganized, whereas information is organized.
>  Data points are individual and sometimes unrelated; information maps out data to provide a big-picture view.
>  Data on its own is meaningless, but when analyzed and interpreted, it becomes meaningful information.
> Data does not depend on information, but information depends on data.
> Data typically comes in the form of graphs, numbers, figures, or statistics, while information is presented through words, language, thoughts, and ideas.
>  Data isn’t sufficient for decision-making, but information enables decisions.

### What is a database?

> A database is an electronic system where data is stored in a way that it can be easily accessed, managed, and updated. To make real use of data, we need Database Management Systems (DBMS).

### What is a Database Management System (DBMS)?

> A database management system (or DBMS) is essentially nothing more than an electronic system where data is stored. Users of the system are given facilities(programs) to perform several kinds of operations on such a system for either manipulation of the data in the database or the management of the database structure itself.

### Why use a DBMS instead of a file-processing system?

> File-processing systems have major disadvantages, including:
> - Data redundancy and inconsistency
> - Difficulty in accessing data
> - Data isolation- multiple files and formats
> - Integrity problems
> - Atomicity problems
> - Concurrent-access anomalies
> - Security problems
> These disadvantages highlight the advantages of using a DBMS, which addresses these issues effectively.

---

## Dbms Architecture

### What is the purpose of the three-schema architecture in DBMS?

> The three-schema architecture in DBMS provides users with an abstract view of the data, hiding details of how the data is stored and maintained. It enables multiple users to access the same data with personalized views while storing the underlying data only once.

### Describe the Three Schema Architecture of data abstraction.##
> **Physical level/Internal**
> The physical level is the lowest level of data abstraction. It describes how the data are stored using low-level data structures. It includes the physical schema, which describes the physical storage structure of the database, and addresses storage allocation, data compression, and encryption. The goal is to define algorithms that allow efficient access to data.
>  **Logical level/Conceptual level**
> The logical level describes the design of a database at the conceptual level, specifying what data are stored in the database and the relationships among those data. Database administrators (DBAs) use this level to decide what information to keep in the database, with the goal of making it easy to use.
> **View level**
> The view level, or external level, is the highest level of abstraction. It simplifies users’ interaction with the system by providing different views to different end-users.Views also provide a security mechanism to prevent users from accessing certain parts of the database.
> ![image](https://github.com/Akmeena4u/CS-Fundamentals-for-placements/assets/93425334/0f7e0462-3c29-4566-bdf0-341ce5b11d72)

### Differentiate between an instance and a schema in a database context.
> **Instance:** The collection of information stored in the DB at a particular moment is called an instance of DB
> **Schema:** Schema is a structural description of data. it serves as a blueprint for logical level, it explains how data is stored, organized, and accessed within a database
> **Data models:** Data models are a way to implement or describe the design( Schema) of a database at a logical level. these are collections of conceptual tools for describing data, data relationships, data semantics, and consistency constraints. Examples include the ER model, relational model, object-oriented model, and object-relational data model.


### How do application programs access databases?

> Application programs, written in host languages like C/C++, Nodejs, or Java, interact with databases by executing DML statements from the host language. Database drivers such as Open Database Connectivity (ODBC) and Java Database Connectivity (JDBC), Mongodb are provided to send DML/DDL statements to the database and retrieve the results

### What are the roles and responsibilities of a Database Administrator (DBA)?

> A Database Administrator (DBA) has central control over the data and the programs that access the data. Responsibilities include schema definition, storage structure and access methods, schema and physical organization modifications, authorization control, and routine maintenance such as periodic backups, security patches, and upgrades.

### Describe the DBMS Application Architectures in DBMS application architectures.
> In T1 architecture, the client, server, and database are all present on the same machine.
> T2 architecture partitions the application into two components. The client machine invokes DB system functionality at the server end through query language statements, using API standards like ODBC and JDBC to interact between client and server.
> T3 architecture partitions the application into three logical components. The client machine acts as a frontend without any direct database calls, communicating with the application server, which in turn communicates with the database system to access data. Advantages of T3 architecture include scalability due to distributed application servers, data integrity by acting as a middle layer between client and database, and enhanced security as clients cannot directly access the database.

---
## ER Model


### What is an ER Model, and what does it represent?

> An ER (Entity-Relationship) model is a diagrammatic tool used in database design to visually represent the structure of a database. It shows the relationships between different real-world objects(entities) in the database. The graphical representation of an ER Model is an ER diagram, which acts as a blueprint of the database.

### Define key terminologies of an ER Model.

> **Entity:** An entity is a “thing” or “object” in the real world that is distinguishable from all other objects. It has a physical existence and can be uniquely identified. For example, each student in a college is an entity.
> **Entity types-Strong v/s Weak** A strong entity can be uniquely identified by its own attributes, typically a primary key. In contrast, a weak entity cannot be uniquely identified by its own attributes and depends on a strong entity for its identification. For example, a Loan is a strong entity, while Payment, which depends on the Loan, is a weak entity.
> **Entity set:** An entity set is a collection of entities of the same type that share the same properties or attributes. For example, "Student" is an entity set consisting of all students in a college.
> **Attributes:** Attributes are properties or characteristics that describe entities. attribute types are as follows:
> - **Simple Attribute:** Cannot be divided further. Example: Customer’s account number.
> - **Composite Attribute:** Can be divided into subparts. Example: Name (first-name, middle-name, last-name).
> - **Single-valued Attribute:** Has only one value. Example: Student ID.
> - **Multi-valued Attribute:** Has more than one value. Example: Phone numbers.
> - **Derived Attribute:** Value can be derived from other attributes. Example: Age.
> - **NULL Value:** Indicates absence of value or not applicable. Example: Middle name if not present.

### What are relationships in an ER Model? Give examples.
> Relationships are associations among two or more entities. Examples include A person owning a vehicle. Relationships could have multiple types as follows:
> Degrees of relationships indicate the number of entities participating in a relationship:
> - **Unary Relationship:** Involves only one entity. Example: Employee manages employee.
> - **Binary Relationship:** Involves two entities. Example: Student takes Course.
> - **Ternary Relationship:** Involves three entities. Example: Employee works on a branch, Employee works on a job.
> Binary relationships are the most common.

### What are Relationship constraints in the ER Model?
> Relationship constraints define rules or conditions that must be satisfied between entities connected by relationships. These constraints ensure the integrity and accuracy of the data within the database. Here are the common types of relationship constraints:
> 
> **1. Mapping cardinality** It specifies how many instances of one entity can be linked to instances of another entity.
> - **One to One:** An entity in set A is associated with at most one entity in set B, and vice versa. Example: Citizen has Aadhar Card.
> - **One to Many:** An entity in set A is associated with multiple entities in set B, but an entity in set B is associated with at most one entity in set A. Example: Citizen has Vehicle.
> - **Many to One:** Multiple entities in set A are associated with one entity in set B, but an entity in set B is associated with at most one entity in set A. Example: Course taken by Professor.
> - **Many to Many:** Multiple entities in set A are associated with multiple entities in set B, and vice versa. Example: Customer buys product.
>
> **2.Participation Constraints** Participation constraints, also known as minimum cardinality constraints, indicate whether all or only some entity instances participate in a relationship. The types are:
> - **Partial Participation:** Not all entities are involved in the relationship instance. Example: Not all customers borrow loans.
> - **Total Participation:** Each entity must be involved in at least one relationship instance. Example: Every loan must be associated with a customer.

### Why do weak entities have a total participation constraint?

> Weak entities have a total participation constraint because they cannot exist without being associated with a strong entity. They rely on the strong entity for identification and existence. For example, a Payment entity (weak entity) cannot exist without being associated with a Loan entity (strong entity).

## Extended ER features

### What is Specialisation in the context of an Extended ER Model?

> Specialisation is a process in the ER model where an entity set is divided into several sub-entity sets based on their unique characteristics or functionalities.
> It's a top-down approach where a superclass (e.g., Person) is divided into subclasses (e.g., Customer, Student, Employee) based on specific attributes or roles. This division helps in representing distinct features and refining the database schema efficiently.
> Specialisation is used to handle situations where certain attributes are only applicable to a subset of entities within a parent entity set

### What is Generalisation in the Extended ER Model?

> Generalisation in the ER model is the reverse process of Specialisation. It involves identifying common attributes shared among multiple entity sets and creating a more generalized superclass to avoid redundancy and streamline the database structure. For example, grouping entities like Car, Jeep, and Bus under a common superclass "Vehicle" to manage shared attributes.

### How does Attribute Inheritance and participation inheritance work in Specialisation and Generalisation?

> **Attribute Inheritance** Both Specialisation and Generalisation involve attribute inheritance, where lower-level entity sets inherit attributes from higher-level entity sets.  This inheritance helps in maintaining consistency and reducing data duplication across related entity sets.
> **Participation Inheritance** If a parent entity set participates in a relationship then its child entity sets will also participate in that relationship

### Explain Aggregation in the context of the Extended ER Model.

> Aggregation is a technique in the ER model used to represent relationships among relationships. It abstracts complex relationships into higher-level entities or "abstract entities," which can then participate in relationships themselves. This approach helps in simplifying the database structure, avoiding redundancy, and improving the overall clarity of relationships within the schema.

### What is ER Diagram symbols and notions ?
> ![image](https://github.com/Akmeena4u/CS-Fundamentals-for-placements/assets/93425334/4239c7f1-b01b-4699-9d92-92b497ccaa9f)



---
---
## Relational Model

### What is the Relational Model and how does it organize data?

> **Answer:** The Relational Model organizes data into tables (relations), where each table has a unique name and consists of rows (tuples) that represent individual data points(relation). Columns in these tables represent attributes, each with its own domain of permissible values.

### What are the key properties that define a table in the Relational Model?

> **Answer:**
> - The table name must be unique within the database.
> - Each attribute value must be atomic (indivisible).
> - Attributes (columns) must have unique names.
> - Every tuple (row) in a table must be unique.
> - The order of rows and columns is not significant.
> - Tables must adhere to integrity constraints to maintain data consistency.

### What are relational keys and its types in the Relational Model.
  
> **Relational keys:** Relational keys are attributes or sets of attributes that uniquely identify each tuple (row) within a relational table. They enforce uniqueness and help establish relationships between tables. The main types of relational keys include:
> - **Super Key (SK):** Any P&C of attributes present in a table that can uniquely identify each tuple.
> - **Candidate Key (CK):** minimum subset of super keys, which can uniquely identify each tuple. so basically It is a super key with no repeated attributes . CK value shouldn’t be NULL
> - **Primary Key (PK):** A selected candidate key used to uniquely identify each tuple in a table. It is chosen based on simplicity and efficiency.
> - **Alternate Key(AK):** All CK except PK.
> **Foreign key:** A Foreign Key (FK) in the Relational Model is an attribute or set of attributes in one table that refers to the Primary Key in another table. It establishes relationships between tables by enforcing referential integrity, ensuring that values in the FK match values in the PK of the referenced table.
> **Composite Key:** PK formed using at least 2 attributes.
> **Compound Key:** PK which is formed using 2 FK.
> **Surrogate Key:**Synthetic PK. it is Generated automatically by DB, usually an integer value. May be used as PK.

### Describe Integrity Constraints in the Relational Model and their significance.

> - **Domain Constraints:** Specify permissible values for attributes, ensuring data type consistency.
> - **Entity Constraints:** Require every tuple in a table to have a Primary Key, ensuring uniqueness and non-null values.
> - **Referential Constraints:** Maintain consistency between related tables, where values in a Foreign Key must match values in a Primary Key of another table.
> - **Key constraints:** These refer to rules or conditions that enforce data integrity and define the characteristics of keys within tables. like - NOT NULL, UNIQUE, CHECK,PRIMARY KEY, FOREIGN KEY
> - Integrity constraints prevent accidental corruption of data and ensure the reliability and consistency of the database.


---
---

## Making of ER, ER->RM 

### What are the Steps to make an ER Diagram?

> - Ask requirements to customers or gather requirements from your own
> - Identify Unique Entity sets
> - Identify attributes and their types with respect to each entity
> - Identify relation and relationship constraints among entities -mapping & participation
> - Using above all details form Er diagram

### What is the process of transforming an Entity-Relationship (ER) Model into a Relational Model?

> Converting an ER Model into a Relational Model involves mapping entities, attributes, relationships, and constraints from the ER diagram into tables, columns, and keys in a relational database design. Following steps we can use for this transformation:
> **Strong entities->Tables:** Strong Entities in an ER Diagram are transformed into individual tables in the Relational Model. The entity name becomes the table name, attributes become columns, and the Primary Key (PK) of the entity serves as the table's Primary Key in the relational database.
> **Weak entities->Tables:** Weak Entities are represented as tables that include all their attributes. Additionally, the Primary Key of the corresponding Strong Entity is added as a Foreign Key (FK) in the weak entity's table to establish the relationship. The table's Primary Key is typically a composite key combining the FK and a partial discriminator key unique to the weak entity.
> **Attributes:**
> - **Single-Valued Attributes-> Columns:** These are directly represented as columns in the tables of the Relational Model, corresponding to their attribute names.
> - **Composite Attributes(can be divided) -> Separate columns:** Each component of a composite attribute is represented as a separate column in the original relation, ensuring atomicity and avoiding nested attributes.
> **Multi-valued attributes- >Seprate tabels:** Multivalued Attributes are transformed into separate tables named after the original attribute. These tables include columns for the entity's Primary Key (used as FK), and a column for each value of the multivalued attribute. The table's Primary Key is typically a composite key combining the FK and the name of the multivalued attribute.
> **Generalisation:** Generalisation in the Relational Model can be handled in two main methods:
> - **Method-1:** Create separate tables for each lower-level entity set and main table, including attributes of both the lower-level entity and the higher-level entity (superclass).
> - **Method-2:** For disjoint and complete generalisation, create separate tables for each lower-level entity set, including attributes from both the lower-level entity and the higher-level entity. This method avoids redundancy but may not handle overlapping or incomplete generalisation effectively.

> -  ![image](https://github.com/Akmeena4u/CS-Fundamentals-for-placements/assets/93425334/92926ea0-b484-4292-882f-7efa3f54b92e)


### Explain the concept of Aggregation in the transformation from ER Model to Relational Model.

> **Answer:** Aggregation involves creating a table for the relationship set itself in the Relational Model. Attributes include Primary Keys of the entity sets involved in the aggregation relationship, along with any descriptive attributes specific to the relationship.

