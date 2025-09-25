# MySQL Interview Questions & Answers (Basics)

## 1. What is MySQL and why is it popular in data analytics?

MySQL is an **open-source relational database management system
(RDBMS)** that uses SQL (Structured Query Language) to manage and
manipulate data.\
It is popular in data analytics because: - It is free and widely used.\
- Supports large datasets efficiently.\
- Works well with BI tools (Power BI, Tableau).\
- Strong community support and easy integration.

------------------------------------------------------------------------

## 2. Difference between MySQL and other RDBMS (like PostgreSQL, SQL Server)?

-   **MySQL**: Best for web applications, lightweight, fast read
    performance.\
-   **PostgreSQL**: More advanced features (CTEs, JSONB, Window
    functions), highly standard-compliant.\
-   **SQL Server**: Enterprise-level, tightly integrated with Microsoft
    ecosystem, supports advanced analytics.

------------------------------------------------------------------------

## 3. Explain the difference between SQL and MySQL.

-   **SQL**: A language used to query and manipulate databases.\
-   **MySQL**: A database management system that uses SQL as its query
    language.

Think of SQL as the language, and MySQL as one tool that speaks that
language.

------------------------------------------------------------------------

## 4. What are primary keys and foreign keys?

-   **Primary Key**: A column (or set of columns) that uniquely
    identifies each row in a table. It cannot have `NULL` values.\
-   **Foreign Key**: A column that creates a relationship between two
    tables, referencing the primary key of another table.

------------------------------------------------------------------------

## 5. What are indexes and why are they important?

-   An **index** is a database object that improves the speed of data
    retrieval.\
-   Importance:
    -   Makes `SELECT` queries faster.\
    -   Reduces full table scans.\
    -   Trade-off: Indexes take storage space and slow down
        `INSERT/UPDATE/DELETE`.

------------------------------------------------------------------------

## 6. Difference between CHAR and VARCHAR in MySQL.

-   **CHAR(n)**: Fixed-length string. Always uses `n` characters (padded
    with spaces if shorter). Faster for small, fixed-size data.\
-   **VARCHAR(n)**: Variable-length string. Stores only actual
    characters plus 1--2 bytes for length. Saves space but slightly
    slower.

------------------------------------------------------------------------

## 7. What is the difference between DELETE, TRUNCATE, and DROP?

-   **DELETE**: Removes rows based on a condition. Can be rolled back.\
-   **TRUNCATE**: Removes all rows in a table, cannot filter. Faster
    than DELETE.\
-   **DROP**: Deletes the entire table structure along with data.

------------------------------------------------------------------------

## 8. What are MySQL data types used in analytics?

-   **Numeric**: INT, BIGINT, DECIMAL, FLOAT, DOUBLE\
-   **String**: CHAR, VARCHAR, TEXT\
-   **Date/Time**: DATE, DATETIME, TIMESTAMP, TIME\
-   **Boolean**: TINYINT(1) used for true/false values

------------------------------------------------------------------------

## 9. How do you check the version of MySQL you are using?

``` sql
SELECT VERSION();
```

or check via command line:

``` bash
mysql --version
```

------------------------------------------------------------------------

## 10. What is the difference between OLTP and OLAP databases?

-   **OLTP (Online Transaction Processing)**: Optimized for real-time
    transactions. Examples: Banking, E-commerce.\
-   **OLAP (Online Analytical Processing)**: Optimized for analytics and
    reporting. Supports aggregation, summarization, and complex queries.


## 11. How do you retrieve all records from a table?

``` sql
SELECT * FROM table_name;
```

------------------------------------------------------------------------

## 12. What is the difference between DISTINCT and GROUP BY?

-   `DISTINCT` removes duplicate rows and returns only unique values.\
-   `GROUP BY` groups rows based on column values, often used with
    aggregate functions (`COUNT`, `SUM`, etc.).

Example:

``` sql
SELECT DISTINCT department FROM employees;
SELECT department, COUNT(*) FROM employees GROUP BY department;
```

------------------------------------------------------------------------

## 13. How do you filter data using WHERE?

``` sql
SELECT * FROM employees WHERE salary > 50000;
```

------------------------------------------------------------------------

## 14. Difference between WHERE and HAVING.

-   `WHERE` filters rows **before grouping**.\
-   `HAVING` filters groups **after aggregation**.

Example:

``` sql
SELECT department, AVG(salary)
FROM employees
WHERE salary > 30000
GROUP BY department
HAVING AVG(salary) > 50000;
```

------------------------------------------------------------------------

## 15. How do you use wildcards in MySQL (LIKE, %, \_)?

-   `%` → matches any sequence of characters.\
-   `_` → matches a single character.

Example:

``` sql
SELECT * FROM employees WHERE name LIKE 'A%';  -- starts with A
SELECT * FROM employees WHERE name LIKE '_n%'; -- second letter n
```

------------------------------------------------------------------------

## 16. Write a query to find employees whose name starts with "A".

``` sql
SELECT * FROM employees WHERE name LIKE 'A%';
```

------------------------------------------------------------------------

## 17. How do you sort query results in ascending/descending order?

``` sql
SELECT * FROM employees ORDER BY salary ASC; -- ascending
SELECT * FROM employees ORDER BY salary DESC; -- descending
```

------------------------------------------------------------------------

## 18. What is the difference between LIMIT and TOP?

-   `LIMIT` → MySQL syntax to restrict rows.\
-   `TOP` → SQL Server syntax. MySQL does **not** support `TOP`.

Example in MySQL:

``` sql
SELECT * FROM employees LIMIT 5;
```

------------------------------------------------------------------------

## 19. Write a query to find the 5 highest salaries in a table.

``` sql
SELECT * FROM employees ORDER BY salary DESC LIMIT 5;
```

------------------------------------------------------------------------

## 20. How do you write a query to find duplicates in a table?

``` sql
SELECT name, COUNT(*)
FROM employees
GROUP BY name
HAVING COUNT(*) > 1;
```

------------------------------------------------------------------------

## 21. What does IS NULL and IS NOT NULL do?

-   `IS NULL` → checks if value is missing.\
-   `IS NOT NULL` → checks if value is present.

Example:

``` sql
SELECT * FROM employees WHERE manager_id IS NULL;     -- no manager
SELECT * FROM employees WHERE manager_id IS NOT NULL; -- has manager
```

------------------------------------------------------------------------

## 22. How do you use BETWEEN for filtering?

``` sql
SELECT * FROM employees WHERE salary BETWEEN 30000 AND 60000;
```

------------------------------------------------------------------------

## 23. Difference between IN and EXISTS.

-   `IN` → compares a column with a list/set of values.\
-   `EXISTS` → checks if subquery returns any rows.

Example:

``` sql
SELECT * FROM employees WHERE department_id IN (1,2,3);

SELECT * FROM employees e
WHERE EXISTS (
    SELECT 1 FROM departments d WHERE e.department_id = d.id
);
```

------------------------------------------------------------------------

## 24. How do you alias a column or table in MySQL?

``` sql
SELECT e.name AS employee_name, e.salary
FROM employees e;
```

------------------------------------------------------------------------

## 25. Write a query to find employees who do not belong to any department.

``` sql
SELECT * FROM employees
WHERE department_id IS NULL;
```

## 26. What are different types of joins in MySQL?

-   **INNER JOIN**: Returns only the rows that have matching values in
    both tables.
-   **LEFT JOIN (LEFT OUTER JOIN)**: Returns all rows from the left
    table and matched rows from the right table. Non-matching rows show
    NULLs.
-   **RIGHT JOIN (RIGHT OUTER JOIN)**: Returns all rows from the right
    table and matched rows from the left table. Non-matching rows show
    NULLs.
-   **FULL OUTER JOIN**: MySQL does not directly support it, but it can
    be simulated using `UNION` of LEFT JOIN and RIGHT JOIN.
-   **CROSS JOIN**: Returns the Cartesian product of two tables.

------------------------------------------------------------------------

## 27. Difference between INNER JOIN and OUTER JOIN

-   **INNER JOIN** → Returns only the rows with matching values in both
    tables.\
-   **OUTER JOIN** → Returns all rows from one table and the matched
    rows from the other. Missing matches are filled with NULLs.

------------------------------------------------------------------------

## 28. Explain LEFT JOIN with example

``` sql
SELECT e.emp_id, e.emp_name, d.dept_name
FROM employees e
LEFT JOIN departments d ON e.dept_id = d.dept_id;
```

Returns all employees, even if they don't belong to any department
(NULL for dept_name).

------------------------------------------------------------------------

## 29. Difference between LEFT JOIN and RIGHT JOIN

-   **LEFT JOIN**: All rows from the left table + matched rows from the
    right.\
-   **RIGHT JOIN**: All rows from the right table + matched rows from
    the left.\
    They are mirror images of each other.

------------------------------------------------------------------------

## 30. When would you use CROSS JOIN?

-   When you need all possible combinations (Cartesian product).\
-   Example: Generating a matrix of products and stores to analyze
    availability.

------------------------------------------------------------------------

## 31. Write a query to join three tables

``` sql
SELECT e.emp_name, d.dept_name, l.location_name
FROM employees e
JOIN departments d ON e.dept_id = d.dept_id
JOIN locations l ON d.location_id = l.location_id;
```

------------------------------------------------------------------------

## 32. What is a self-join? Give an example

A self-join is when a table joins with itself.\
Example: Find employees and their managers.

``` sql
SELECT e.emp_name AS Employee, m.emp_name AS Manager
FROM employees e
LEFT JOIN employees m ON e.manager_id = m.emp_id;
```

------------------------------------------------------------------------

## 33. Difference between JOIN and UNION

-   **JOIN** → Combines columns from multiple tables based on
    relationships.\
-   **UNION** → Combines rows from multiple queries/tables (same
    structure).

------------------------------------------------------------------------

## 34. How do you use UNION ALL and what is the difference with UNION?

-   **UNION** → Removes duplicates.\
-   **UNION ALL** → Keeps duplicates.\
    Example:

``` sql
SELECT city FROM customers
UNION
SELECT city FROM suppliers;
```

------------------------------------------------------------------------

## 35. Write a query to find employees who have no manager (self-join scenario)

``` sql
SELECT e.emp_name
FROM employees e
LEFT JOIN employees m ON e.manager_id = m.emp_id
WHERE m.emp_id IS NULL;
```

------------------------------------------------------------------------

## 36. Explain many-to-many relationship and how it is implemented in MySQL

-   Many-to-many requires a **junction (bridge) table**.\
    Example: Students and Courses.\
    Tables: `students`, `courses`, `student_course` (junction with
    student_id, course_id).

------------------------------------------------------------------------

## 37. What is referential integrity in MySQL?

-   Ensures relationships between tables remain consistent.\
-   Enforced using **FOREIGN KEY constraints** (prevents orphan
    records).

------------------------------------------------------------------------

## 38. What happens when you join a table with no matching rows?

-   With **INNER JOIN** → Row is excluded.\
-   With **LEFT/RIGHT JOIN** → Row is included with `NULL` for missing
    values.

------------------------------------------------------------------------

## 39. Write a query using INNER JOIN with ON and USING---what is the difference?

``` sql
-- Using ON
SELECT e.emp_id, e.emp_name, d.dept_name
FROM employees e
INNER JOIN departments d ON e.dept_id = d.dept_id;

-- Using USING (when column name is same)
SELECT e.emp_id, e.emp_name, d.dept_name
FROM employees e
INNER JOIN departments d USING (dept_id);
```

`USING` can only be used when both tables have the same column name.

------------------------------------------------------------------------

## 40. What is an equi-join vs non-equi join?

-   **Equi-join** → Join condition uses `=` operator. (Most common)\
-   **Non-equi join** → Join condition uses operators like `<`, `>`,
    `BETWEEN`.

Example (non-equi join):

``` sql
SELECT e.emp_name, s.grade
FROM employees e
JOIN salary_grades s ON e.salary BETWEEN s.min_salary AND s.max_salary;
```

