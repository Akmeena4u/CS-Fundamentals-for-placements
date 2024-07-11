
### Interview Questions on SQL

1. **What is SQL?**
   > SQL stands for Structured Query Language, which is used to access and manipulate data in relational databases. It provides a standard way of performing CRUD operations: Create, Read, Update, and Delete.

2. **What is an RDBMS?**
   > An RDBMS (Relational Database Management System) is software that allows the creation, maintenance, and management of relational databases based on the relational model. It enables users to define, create, query, update, and administer databases.
   >  Examples of RDBMS include MySQL, Microsoft SQL Server, Oracle Database, IBM Db2, PostgreSQL, etc.

3. **Differentiate between SQL and MySQL.**
   > SQL is a standardized language used for querying and manipulating data in relational databases, whereas MySQL is an open-source Relational Database Management System (RDBMS) that uses SQL as its query language. MySQL not only implements SQL for data operations but also provides features for managing and administering databases.

4. **What are SQL data types used for?**
   > In SQL databases, data is stored in tables with columns that have specific data types. These data types define the kind of data that can be stored in each column, ensuring data integrity and efficient storage.
   > **Some common SQL data types and their usage.**
   > - **CHAR and VARCHAR:** Stores strings with fixed or variable lengths.
   > - **INT, TINYINT, SMALLINT, BIGINT:** Store integer values of different ranges.
   > - **FLOAT, DOUBLE:** Store decimal numbers with different precision levels.
   > - **TEXT and BLOB:** Handle large amounts of text or binary data.
   > - **ENUM(val1, val2, val3, ...):**A string object that can have only one value, chosen from a list of possible values.
   > - **SET(val1, val2, val3, ...)** A string object that can have 0 or more values, chosen from a list of possible values.
   > - **DATE** A date. Format: YYYY-MM-DD.
   > - **DATETIME**A date and time combination. Format: YYYY-MM-DD hh:mm:ss.
   > - **YEAR** A year in four-digit format.

5. **Why are variable-length data types like VARCHAR preferred over fixed-length types like CHAR?**
   > Variable-length data types like VARCHAR occupy storage space only equal to the actual data size stored, whereas fixed-length types like CHAR always use the defined length, which can lead to wastage of storage space.


6. **Explain Types of SQL commands:**
   > 
   > 1. DDL (data definition language): defining relation schema.
   >    1. CREATE: create table, DB, view.
   >    2. ALTER TABLE: modification in table structure. e.g., change column datatype or add/remove columns.
   >    3. DROP: delete table, DB, view.
   >    4. TRUNCATE: remove all the tuples from the table.
   >    5. RENAME: rename DB name, table name, column name, etc.
   > 
   > 2. DRL/DQL (data retrieval language / data query language): retrieve data from the tables.
   >    1. SELECT
   > 
   > 3. DML (data modification language): use to perform modifications in the DB
   >    1. INSERT: insert data into a relation
   >    2. UPDATE: update relation data.
   >    3. DELETE: delete row(s) from the relation.
   > 
   > 4. DCL (Data Control language): grant or revoke authorities from user.
   >    1. GRANT: access privileges to the DB
   >    2. REVOKE: revoke user access privileges.
   > 
   > 5. TCL (Transaction control language): to manage transactions done in the DB
   >    1. START TRANSACTION: begin a transaction
   >    2. COMMIT: apply all the changes and end transaction
   >    3. ROLLBACK: discard changes and end transaction
   >    4. SAVEPOINT: checkout within the group of transactions in which to rollback


7. **What are some key commands and techniques used for managing database data in SQL?**
   > - **Managing Databases (DDL):**
   >   1. `CREATE DATABASE IF NOT EXISTS db-name;` - Creates a new database if it doesn't already exist.
   >   2. `USE db-name;` - Switches to the specified database for executing subsequent commands.
   >   3. `DROP DATABASE IF EXISTS db-name;` - Deletes the specified database if it exists.
   >   4. `SHOW DATABASES;` - Lists all databases on the server.
   >   5. `SHOW TABLES;` - Lists tables in the currently selected database.

8. **What are some key commands and techniques used for Retrieving database data in SQL?**
   > **DATA RETRIEVAL LANGUAGE (DRL):**
   > 
   > 1. **Syntax:**
   >    - `SELECT <set of column names> FROM <table_name>;`
   > 2. **Order of Execution:**
   >    - From RIGHT to LEFT.
   > 3. **Can we use SELECT without FROM clause?**
   >    1. Yes, using DUAL Tables.
   >    2. Dual tables are dummy tables created by MySQL for certain actions without referring to user-defined tables.
   >    3. Examples:
   >       - `SELECT 55 + 11;`
   >       - `SELECT NOW();`
   >       - `SELECT UCASE();` (uppercase function)
   > 4. **WHERE:**
   >    1. Reduces rows based on given conditions.
   >    2. Example: `SELECT * FROM customer WHERE age > 18;`
   > 5. **BETWEEN:**
   >    1. Example: `SELECT * FROM customer WHERE age BETWEEN 0 AND 100;` (inclusive)
   > 6. **IN:**
   >    1. Reduces OR conditions.
   >    2. Example: `SELECT * FROM officers WHERE officer_name IN ('Lakshay', 'Maharana Pratap', 'Deepika');`
   > 7. **AND/OR/NOT:**
   >    1. AND: `WHERE cond1 AND cond2`
   >    2. OR: `WHERE cond1 OR cond2`
   >    3. NOT: `WHERE col_name NOT IN (1,2,3,4);`
   > 8. **IS NULL:**
   >    - Example: `SELECT * FROM customer WHERE prime_status IS NULL;`
   > 9. **Pattern Searching / Wildcard (`%`, `_`):**
   >    1. `%`: Matches any number of characters (like `*` in regex).
   >    2. `_`: Matches a single character.
   >    3. Example: `SELECT * FROM customer WHERE name LIKE '%p_';`
   > 10. **ORDER BY:**
   >     1. Sorting retrieved data using the WHERE clause.
   >     2. Example: `SELECT * FROM customer ORDER BY name DESC;` (DESC = Descending, ASC = Ascending)
   > 11. **GROUP BY:**
   >     1. Collects data and groups results by one or more columns.
   >     2. Example: `SELECT c1, c2, c3 FROM sample_table WHERE cond GROUP BY c1, c2, c3;`
   >     3. Requires all selected columns to be in the GROUP BY clause when not using aggregation functions.
   >     4. Used with aggregation functions like COUNT(), SUM(), AVG(), MIN(), MAX().
   > 12. **DISTINCT:**
   >     1. Finds distinct values in a table.
   >     2. Example: `SELECT DISTINCT(col_name) FROM table_name;`
   > 13. **GROUP BY HAVING:**
   >     1. Filters groups based on specified conditions after GROUP BY.
   >     2. Example: `SELECT COUNT(cust_id), country FROM customer GROUP BY country HAVING COUNT(cust_id) > 50;`
   > 14. **WHERE vs HAVING:**
   >     1. Both filter rows based on conditions.
   >     2. WHERE is used before GROUP BY, HAVING is used after.
   >     3. HAVING requires GROUP BY.
   > 

9. **What are some key commands and techniques used for the definition database data in SQL?**
   > **CONSTRAINTS (DDL):**
   > 
   > 1. **Primary Key:**
   >    1. PK is not null, unique, and only one per table.
   > 
   > 2. **Foreign Key:**
   >    1. FK refers to PK of another table.
   >    2. Each relation can have any number of FKs.
   >    3. Example:
   >       ```
   >       CREATE TABLE ORDER (
   >           id INT PRIMARY KEY,
   >           delivery_date DATE,
   >           order_placed_date DATE,
   >           cust_id INT,
   >           FOREIGN KEY (cust_id) REFERENCES customer(id)
   >       );
   >       ```
   > 
   > 3. **UNIQUE:**
   >    1. Unique, can be null, and a table can have multiple unique attributes.
   >    2. Example:
   >       ```
   >       CREATE TABLE customer (
   >           ...
   >           email VARCHAR(1024) UNIQUE,
   >           ...
   >       );
   >       ```
   > 
   > 4. **CHECK:**
   >    1. Example:
   >       ```
   >       CREATE TABLE customer (
   >           ...
   >           CONSTRAINT age_check CHECK (age > 12),
   >           ...
   >       );
   >       ```
   > 
   > 5. **DEFAULT:**
   >    1. Set default value of the column.
   >    2. Example:
   >       ```
   >       CREATE TABLE account (
   >           ...
   >           saving_rate DOUBLE NOT NULL DEFAULT 4.25,
   >           ...
   >       );
   >       ```
   > 
   > 6. An attribute can be PK and FK both in a table.
   > 
   > 7. **ALTER OPERATIONS:**
   >    1. Changes schema.
   >    2. **ADD:**
   >       ```
   >       ALTER TABLE table_name ADD new_col_name datatype ADD new_col_name_2 datatype;
   >       ```
   >    3. **MODIFY:**
   >       ```
   >       ALTER TABLE table-name MODIFY col-name col-datatype;
   >       ```
   >    4. **CHANGE COLUMN:**
   >       ```
   >       ALTER TABLE table-name CHANGE COLUMN old-col-name new-col-name new-col-datatype;
   >       ```
   >    5. **DROP COLUMN:**
   >       ```
   >       ALTER TABLE table-name DROP COLUMN col-name;
   >       ```
   >    6. **RENAME:**
   >       ```
   >       ALTER TABLE table-name RENAME TO new-table-name;
   >       ```


 10. **What are some key commands and techniques used for the Manipulation of database data in SQL?** 
      > **DATA MANIPULATION LANGUAGE (DML):**
      > 
      > 1. **INSERT:**
      >    - Inserting values into a table.
      >    ```
      >    INSERT INTO table-name(col1, col2, col3) VALUES (v1, v2, v3), (val1, val2, val3);
      >    ```
      > 
      > 2. **UPDATE:**
      >    - Updating existing records in a table.
      >    ```
      >    UPDATE table-name SET col1 = 1, col2 = 'abc' WHERE id = 1;
      >    ```
      >    - Updating multiple rows:
      >    ```
      >    UPDATE student SET standard = standard + 1;
      >    ```
      > 
      > 3. **ON UPDATE CASCADE:**
      >    - Automatically updates foreign key values in related tables when primary key values are updated.
      >    - Example:
      >      ```
      >      CREATE TABLE ORDER (
      >          order_id INT PRIMARY KEY,
      >          delivery_date DATE,
      >          cust_id INT,
      >          FOREIGN KEY (cust_id) REFERENCES customer(id) ON UPDATE CASCADE
      >      );
      >      ```
      > 
      > 4. **DELETE:**
      >    - Deleting records from a table.
      >    ```
      >    DELETE FROM table-name WHERE id = 1;
      >    ```
      >    - Deleting all rows:
      >    ```
      >    DELETE FROM table-name;
      >    ```
      >    - **DELETE CASCADE:**
      >      - Automatically deletes child entries in related tables when parent entries are deleted.
      >      - Example:
      >        ```
      >        CREATE TABLE ORDER (
      >            order_id INT PRIMARY KEY,
      >            delivery_date DATE,
      >            cust_id INT,
      >            FOREIGN KEY (cust_id) REFERENCES customer(id) ON DELETE CASCADE
      >        );
      >        ```
      >    - **ON DELETE SET NULL:**
      >      - Sets foreign key values to NULL in related tables when parent entries are deleted.
      >      - Example:
      >        ```
      >        CREATE TABLE ORDER (
      >            order_id INT PRIMARY KEY,
      >            delivery_date DATE,
      >            cust_id INT,
      >            FOREIGN KEY (cust_id) REFERENCES customer(id) ON DELETE SET NULL
      >        );
      >        ```
      > 
      > 5. **REPLACE:**
      >    - Replaces existing rows or inserts new rows in a table.
      >    - Example using REPLACE INTO:
      >      ```
      >      REPLACE INTO student (id, class) VALUES (4, 3);
      >      ```
      >    - Example using REPLACE INTO with SET:
      >      ```
      >      REPLACE INTO table SET col1 = val1, col2 = val2;
      >      ```
  
   
   

