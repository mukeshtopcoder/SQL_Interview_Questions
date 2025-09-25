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
