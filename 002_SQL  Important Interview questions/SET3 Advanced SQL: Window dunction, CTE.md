
### Table of Contents

<!-- TOC_START -->
| No. | Questions |
| --- | --------- |
| 1   | [Explain all about window functions in SQL, their syntax, use cases, and examples of types](#explain-all-about-window-functions-in-sql-their-syntax-use-cases-and-examples-of-types) |
| 2   | [Explain the use of a CASE expression in SQL queries, with examples](#explain-the-use-of-a-case-expression-in-sql-queries-with-examples) |
| 3   | [Explain what a Common Table Expression (CTE) is in SQL, with examples](#explain-what-a-common-table-expression-cte-is-in-sql-with-examples) |


### Explain all about window functions in SQL, their syntax, use cases, and examples of types
> Window functions in SQL are special functions that allow you to perform calculations across a set of table rows related to the current row. Unlike normal aggregate functions like SUM() or AVG(), window functions do not collapse rows into a single result. Instead, they keep each row separate and add useful information to each row without changing the overall result set. You can use window functions to calculate rankings, running totals, compare values with others, or get values from previous or next rows in a query. They're really handy for analyzing data in more complex ways without grouping rows together.

#### Window Function Syntax:

```sql
SELECT <Col-names>,
<window_function>() OVER (
[PARTITION BY partition_expression]
[ORDER BY order_expression [ASC | DESC]]


#### 1. Can you explain what window functions are in SQL, their syntax, and use cases, and provide examples of their types?
>
> Window functions in SQL are special functions that allow you to perform calculations across a set of table rows related to the current row. Unlike normal aggregate functions like `SUM()` or `AVG()`, window functions do not collapse rows into a single result. Instead, they keep each row separate and add useful information to each row without changing the overall result set. You can use window functions to calculate rankings, running totals, compare values with others, or get values from previous or next rows in a query. They're really handy for analyzing data in more complex ways without grouping rows together.
>
> ### Window Function Syntax:
> ```
> SELECT <Col-names>,
> <window_function>() OVER (
>     [PARTITION BY partition_expression]
>     [ORDER BY order_expression [ASC | DESC]]
>     [ROWS/RANGE clause]
> )
> FROM <Table-name>
> ```
> - **PARTITION BY**: Divides the result set into partitions to which the window function is applied independently
> - **ORDER BY**: Specifies the order of rows within each partition.
> - **ROWS/RANGE clause**: Defines the window frame within a partition for the function calculation.
>
> ### Use Cases:
> Window functions are used for:
> - Ranking rows within a partition.
> - Calculating running totals or moving averages.
> - Comparing rows with preceding or following rows.
> - Aggregating values within specific groups.
>
> ### Types of Window Functions:
>
> #### 1. Aggregate Functions:
> - Operate over a set of rows and return a single value per row.
> - Examples: `SUM()`, `AVG()`, `MIN()`, `MAX()`.
>   
>   > **Example:**
>   > ```sql
>   > SELECT department_id, employee_name, salary,
>   >        AVG(salary) OVER (PARTITION BY department_id) AS avg_salary
>   > FROM employees;
>   > ```
>
> #### 2. Ranking Functions:
> - Assign a rank to each row based on a specified order.
> - Examples: `ROW_NUMBER()`, `RANK()`, `DENSE_RANK()`.
>   
>   > **Example:**
>   > ```sql
>   > SELECT employee_name, department_id, salary,
>   >        RANK() OVER (PARTITION BY department_id ORDER BY salary DESC) AS rank
>   > FROM employees;
>   > ```
>
>   - **ROW_NUMBER()**: Assigns a unique sequential integer to each row within a partition.
>   
>   > **Example:**
>   > ```sql
>   > SELECT employee_name, department_id, salary,
>   >        ROW_NUMBER() OVER (PARTITION BY department_id ORDER BY salary DESC) AS row_num
>   > FROM employees;
>   > ```
>
>   - **RANK()**: Assigns a rank to each row within a partition, with gaps in the ranking sequence in case of ties.
>   
>   > **Example:**
>   > ```sql
>   > SELECT employee_name, department_id, salary,
>   >        RANK() OVER (PARTITION BY department_id ORDER BY salary DESC) AS rank
>   > FROM employees;
>   > ```
>
>   - **DENSE_RANK()**: Assigns a rank to each row within a partition, without gaps in the ranking sequence.
>   
>   > **Example:**
>   > ```sql
>   > SELECT employee_name, department_id, salary,
>   >        DENSE_RANK() OVER (PARTITION BY department_id ORDER BY salary DESC) AS dense_rank
>   > FROM employees;
>   > ```
>
> #### 3. Value Functions:
> - Retrieve data from a different row relative to the current row.
> - Examples: `LAG()`, `LEAD()` , `FIRST_VALUE()`.
>
>   - **LAG()**: Accesses data from a previous row within the same result set.
>   
>   > **Example:**
>   > ```sql
>   > SELECT employee_name, salary,
>   >        LAG(salary, 1) OVER (ORDER BY employee_id) AS previous_salary
>   > FROM employees;
>   > ```
>
>   - **LEAD()**: Accesses data from a subsequent row within the same result set.
>   
>   > **Example:**
>   > ```sql
>   > SELECT employee_name, salary,
>   >        LEAD(salary, 1) OVER (ORDER BY employee_id) AS next_salary
>   > FROM employees;
>   > ```
>
> #### Practical questions
>
>    > **Query to rank employees by their salary within each department**
>    > ```
>    > SELECT name, department_id, salary,
>    >    RANK() OVER(PARTITION BY department_id ORDER BY salary DESC) AS salary_rank
>    > FROM employees;
>    >```

### Summary:
> Window functions provide a powerful way to perform complex calculations and analysis in SQL. They allow for detailed insight into data relationships without altering the structure of the result set. By partitioning and ordering rows, window functions enable precise control over how calculations are applied, making them indispensable for advanced querying and reporting tasks.


---



## Case Expressions

#### 2. Can you explain the use of a CASE expression in SQL queries? Provide an example where a CASE expression would be beneficial over using traditional conditional statements.
> A CASE expression in SQL allows for conditional logic within a query. It's particularly useful when you need to perform conditional checks and return different values based on those conditions, all within a single query. Unlike traditional IF-ELSE statements, CASE expressions can be used within SELECT, WHERE, ORDER BY, and GROUP BY clauses to manipulate data based on specified conditions.
>
> **Example Answer:**
> 
> ```sql
> SELECT
>    employee_id,
>    first_name,
>    last_name,
>   salary,
>    CASE
>        WHEN salary >= 10000 THEN 'High Salary'
>        WHEN salary >= 5000 AND salary < 10000 THEN 'Medium Salary'
>        ELSE 'Low Salary'
>    END AS salary_category
> FROM
>    employees;
> ```
>
> In this example, the CASE expression categorizes employees based on their salary into 'High Salary', 'Medium Salary', or 'Low Salary' categories. This approach is efficient and concise compared to using multiple IF-ELSE statements or procedural code to achieve the same result.
>
> ### Summary:
> - **CASE Statement:** Used for executing multiple statements or actions based on different conditions.
> - **CASE Expression:** Used for returning a single value based on specified conditions within a SELECT statement.


---

## Common Table Expressions (CTEs)

#### 3. Can you explain what a Common Table Expression (CTE) is in SQL?
>
> A Common Table Expression (CTE) in SQL is a temporary result set that you can reference within a SELECT, INSERT, UPDATE, or DELETE statement. It helps improve readability and simplify complex queries by breaking them into smaller, more manageable parts. Unlike subqueries, CTEs can be self-referencing and can be referenced multiple times within a query.
>
> **Example Answer:**
> 
> ```sql
> -- Example using CTE to find employees with salaries above the average salary
> 
> WITH avg_salary_cte AS (
>    SELECT AVG(salary) AS avg_salary
>    FROM employees
> )
> SELECT name, salary
> FROM employees
> WHERE salary > (SELECT avg_salary FROM avg_salary_cte);
> ```
>
> In this example, the CTE `avg_salary_cte` calculates the average salary of employees, which is then used to filter employees with salaries above the average. Using a CTE here improves query clarity and avoids repeating the average calculation.

