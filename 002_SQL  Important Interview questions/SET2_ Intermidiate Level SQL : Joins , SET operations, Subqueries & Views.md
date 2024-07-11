
1. **Explain all about joins in SQL**
  
    > **JOINING TABLES:**
    > 
    > 1. All RDBMS are relational in nature, where tables are referenced to obtain meaningful outcomes.
    > 
    > 2. Foreign keys (FK) are used to reference other tables.
    > 
    > 3. **INNER JOIN:**
    >    - Returns a resultant table with matching values from both tables.
    >    - Syntax:
    >      ```
    >      SELECT column-list FROM table1 INNER JOIN table2 ON condition1
    >      INNER JOIN table3 ON condition2 ...;
    >      ```
    > 
    > 4. **Alias in MySQL (AS):**
    >    - Provides a temporary name to tables or columns in a query for readability.
    >    - Example:
    >      ```
    >      SELECT col_name AS alias_name FROM table_name;
    >      SELECT col_name1, col_name2,... FROM table_name AS alias_name;
    >      ```
    > 
    > 5. **OUTER JOIN:**
    >    - **LEFT JOIN:**
    >      - Returns all data from the left table and matched data from the right table.
    >      - Example:
    >        ```
    >        SELECT columns FROM table1 LEFT JOIN table2 ON Join_Condition;
    >        ```
    >    - **RIGHT JOIN:**
    >      - Returns all data from the right table and matched data from the left table.
    >      - Example:
    >        ```
    >        SELECT columns FROM table1 RIGHT JOIN table2 ON join_cond;
    >        ```
    >    - **FULL JOIN:**
    >      - Returns all data when there is a match in either left or right table data.
    >      - Emulated using LEFT JOIN UNION RIGHT JOIN.
    > 
    > 6. **UNION ALL vs UNION:**
    >    - **UNION ALL:** Includes duplicate values.
    >    - **UNION:** Provides unique values.
    > 
    > 7. **CROSS JOIN:**
    >    - Returns the Cartesian product of data from both tables.
    >    - Example:
    >      ```
    >      SELECT column-lists FROM table1 CROSS JOIN table2;
    >      ```
    > 
    > 8. **SELF JOIN:**
    >    - Used to join a table to itself to retrieve related data.
    >    - Example:
    >      ```
    >      SELECT columns FROM table AS t1 INNER JOIN table AS t2 ON t1.id = t2.id;
    >      ```
    > 
    > 9. **Join without using JOIN keywords:**
    >    - Implicitly joins tables based on specified conditions.
    >    - Example:
    >      ```
    >      SELECT artist_name, album_name, year_recorded FROM artist, album WHERE artist.id = album.artist_id;
    >      ```
    > 
    >   These methods are used to combine data from multiple tables in SQL queries.



2. **Explain all about SET Operations in SQL**
     
    > **SET OPERATIONS:** These operations are useful for combining and comparing data from multiple tables in SQL queries.
    > 1. Used to combine results from multiple SELECT statements.
    > 
    > 2. Always returns distinct rows.
    > 
    > 3. **UNION:**
    >    - Combines the results of two or more SELECT statements.
    >    - Example:
    >      ```
    >      SELECT * FROM table1
    >      UNION
    >      SELECT * FROM table2;
    >      ```
    >    - Note: Number of columns and their order must be the same in both SELECT statements.
    > 
    > 4. **INTERSECT:**
    >    - Returns common values between two tables.
    >    - Emulated with INNER JOIN:
    >      ```
    >      SELECT DISTINCT column-list FROM table-1 INNER JOIN table-2 USING(join_cond);
    >      ```
    >    - Example:
    >      ```
    >      SELECT DISTINCT * FROM table1 INNER JOIN table2 USING(id);
    >      ```
    > 
    > 5. **MINUS:**
    >    - Returns rows from the first table that do not exist in the second table.
    >    - Emulated with LEFT JOIN and WHERE condition:
    >      ```
    >      SELECT column_list FROM table1 LEFT JOIN table2 ON condition WHERE table2.column_name IS NULL;
    >      ```
    >    - Example:
    >      ```
    >      SELECT id FROM table-1 LEFT JOIN table-2 USING(id) WHERE table-2.id IS NULL;
    >      ```
    
3. **Explain Join V/S SET?**

   ![image](https://github.com/user-attachments/assets/356001dc-22d9-4a0b-8c59-bec14ff0006a)

---

## Sub Queries




