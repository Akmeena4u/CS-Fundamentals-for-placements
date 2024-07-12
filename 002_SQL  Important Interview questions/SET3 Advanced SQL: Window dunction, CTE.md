

### Interview Question: Window Functions in SQL

**Question:**
> Can you explain what window functions are in SQL, their syntax, and use cases, and provide examples of their types?

**Answer:**
> **Window functions** in SQL operate on a set of rows and return a single value for each row from the underlying query. They perform calculations across a set of table rows related to the current row. Window functions do not cause rows to become grouped into a single output row like aggregate functions do. Instead, rows retain their separate identities. The typical syntax for a window function includes an `OVER` clause which defines the window of rows that the function will operate on.
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

> #### Practical questions
>
>   **Query to rank employees by their salary within each department**
> ```
> SELECT name, department_id, salary,
>       RANK() OVER(PARTITION BY department_id ORDER BY salary DESC) AS salary_rank
> FROM employees;
```

### Summary:
> Window functions provide a powerful way to perform complex calculations and analysis in SQL. They allow for detailed insight into data relationships without altering the structure of the result set. By partitioning and ordering rows, window functions enable precise control over how calculations are applied, making them indispensable for advanced querying and reporting tasks.
