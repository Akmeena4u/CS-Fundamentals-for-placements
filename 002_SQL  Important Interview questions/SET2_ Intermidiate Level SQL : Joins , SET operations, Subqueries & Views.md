
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
    > 
    > ![image](https://github.com/user-attachments/assets/d03bd8a6-32cd-4886-9708-71151562957a)




---
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


## Subqueries

1. **What is a subquery and how does it differ from a join?**
   > A subquery is a query nested within another query. It is used to return data that will be used in the main query as a condition to further restrict the data to be retrieved. Unlike joins, which combine columns from multiple tables, subqueries can be used to filter rows from a single table.


2. **What are the main clauses where subqueries can be used?**
     > Subqueries can be used in the following clauses:
   > 1. Inside a WHERE clause.
   >  > ```sql
   > SELECT * FROM table1 WHERE col1 IN (SELECT col1 FROM table1);
   > ```
   > This query selects all rows from `table1` where `col1` is present in the result of the inner subquery.
   > 
   > 2. Inside a FROM clause.
   >  ```sql
   > SELECT MAX(rating) FROM (SELECT * FROM movie WHERE country = 'India') as temp;
   > ```
   > This query finds the maximum rating from movies where the country is 'India'.
   > A derived subquery, also known as a derived table, is used in the FROM clause. It acts as a temporary table created for the duration of the main query.
   > 
   > 3. Inside a SELECT clause.
   > ```sql
   > SELECT (SELECT column_list(s) FROM T_name WHERE condition), columnList(s) FROM T2_name WHERE condition;
   > ```
   > This query includes a subquery in the SELECT clause to fetch data from `T_name` along with columns from `T2_name`.



3. **How many types of subqueries are there in SQL based on the number of rows they return?:**
    > Subqueries in SQL can also be classified based on the number of rows they return. The main types are:

   > 1. **Single-row Subquery:**
   > A single-row subquery returns only one row of results. It is typically used with comparison operators like `=`, `>`, `<`.
   > 
   > **Example:**
   > ```sql
   > SELECT employee_name 
   > FROM employees 
   > WHERE salary = (SELECT MAX(salary) FROM employees);
   > ```
   > This query retrieves the name of the employee with the highest salary.
   >
   > 2. **Multiple-row Subquery:**
   > A multiple-row subquery returns more than one row of results. It is typically used with operators like `IN`, `ANY`, `ALL`.
   > 
   > **Example:**
   > ```sql
   > SELECT employee_name 
   > FROM employees 
   > WHERE department_id IN (SELECT department_id 
   >                         FROM departments 
   >                         WHERE location_id = 1700);
   > ```
   > This query retrieves the names of employees who work in departments located in location 1700.
   >
   > 3. **Correlated Subquery:**
   > A correlated subquery references columns from the outer query and is executed once for each row processed by the outer query.
   > 
   > **Example:**
   > ```sql
   > SELECT employee_name 
   > FROM employees e1 
   > WHERE salary > (SELECT AVG(salary) 
   >                 FROM employees e2 
   >                 WHERE e1.department_id = e2.department_id);
   > ```
   > This query retrieves the names of employees whose salary is above the average salary of their department.
   >
   > 4. **Nested Subquery:**
   > A nested subquery is a subquery within another subquery. It allows for more complex querying by layering conditions.
   > 
   > **Example:**
   > ```sql
   > SELECT employee_name 
   > FROM employees 
   > WHERE department_id = (SELECT department_id 
   >                        FROM departments 
   >                        WHERE manager_id = (SELECT manager_id 
   >                                            FROM managers 
   >                                            WHERE manager_name = 'John Doe'));
   > ```
   > This query retrieves the names of employees who work in the department managed by 'John Doe'.
   > These classifications help in understanding the different ways subqueries can be utilized to handle various data retrieval requirements in SQL.



4. **What are the restrictions on subqueries in SQL?**
   > - A subquery must be enclosed in parentheses.
   > - A subquery must appear on the right side of the comparison operator.
   > - In a WHERE or HAVING clause, a subquery cannot use the ORDER BY clause, but it can be used in subqueries within the FROM clause.

5. **How can you use subqueries with the EXISTS operator?**
   > The EXISTS operator is used to test for the existence of any record in a subquery. It returns true if the subquery returns one or more records.
   > ```sql
   > SELECT name
   > FROM employees e
   > WHERE EXISTS (SELECT 1 FROM departments d WHERE e.department_id = d.id);
   > ```


6. **Write a query to find employees who earn more than the average salary of their department.**
   > ```sql
   > SELECT name
   > FROM employees e
   > WHERE salary > (SELECT AVG(salary) FROM employees WHERE department_id = e.department_id);
   > ```

7. **What is the difference between a subquery and a join?**
   > A subquery is a query within another query, often used to return a single value or a list of values to be used in the main query. A join combines rows from two or more tables based on a related column between them, and it typically produces a result set with columns from both tables.
   > Here is the detailed difference between JOIN and Subquery in tabular form:

| Criteria                   | JOIN                                                                                                           | Subquery                                                                                                      |
|----------------------------|---------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------|
| Definition                 | > Combines rows from two or more tables based on a related column between them.                                | > A query nested within another query.                                                                        |
| Usage                      | > Used to retrieve data from multiple tables in a single query.                                                | > Used to perform operations that need results from another query.                                            |
| Syntax                     | > `SELECT columns FROM table1 JOIN table2 ON table1.column = table2.column;`                                   | > `SELECT columns FROM table1 WHERE column = (SELECT column FROM table2 WHERE condition);`                    |
| Performance                | > Generally faster for large datasets as it directly combines tables.                                          | > Can be slower for large datasets as the inner query is executed for each row of the outer query.            |
| Readability                | > Can be more readable and easier to understand, especially for complex queries involving multiple tables.     | > Can become complex and harder to read when nested deeply.                                                   |
| Result Set                 | > Produces a result set with columns from both or all joined tables.                                           | > Produces a result set from the outer query, which can be influenced by the result of the subquery.          |
| Types                      | > INNER JOIN, LEFT JOIN, RIGHT JOIN, FULL JOIN                                                                 | > Single-row subquery, Multiple-row subquery, Correlated subquery, Nested subquery                            |
| Correlated Subqueries      | > Not applicable.                                                                                              | > Correlated subqueries are subqueries that reference columns from the outer query.                           |
| Use Case Example           | > Joining employees with their respective departments:                                                         | > Finding employees whose salary is above the average salary of their department:                             |
| Example                    | > ```sql<br>SELECT e.name, d.name<br>FROM employees e<br>JOIN departments d ON e.department_id = d.id;<br>``` | > ```sql<br>SELECT name<br>FROM employees<br>WHERE salary > (SELECT AVG(salary) FROM employees);<br>```      |


