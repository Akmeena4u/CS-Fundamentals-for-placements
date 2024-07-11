
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
  
