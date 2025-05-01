# SQL Cheatsheet: From Beginner to Advanced

## Table of Contents
1. [Basic SQL Syntax](#basic-sql-syntax)
   - [SELECT Statement](#select-statement)
   - [WHERE Clause](#where-clause)
   - [ORDER BY](#order-by)
   - [LIMIT/OFFSET](#limitoffset-pagination)
2. [Data Manipulation](#data-manipulation)
   - [INSERT Statement](#insert-statement)
   - [UPDATE Statement](#update-statement)
   - [DELETE Statement](#delete-statement)
3. [Data Definition](#data-definition)
   - [CREATE TABLE](#create-table)
   - [ALTER TABLE](#alter-table)
   - [DROP TABLE](#drop-table)
4. [Common Data Types](#common-data-types)
   - [Numeric Types](#numeric-types)
   - [String Types](#string-types)
   - [Date/Time Types](#datetime-types)
   - [Other Types](#other-types)
5. [Table Relationships and Joins](#table-relationships-and-joins)
   - [INNER JOIN](#inner-join)
   - [LEFT JOIN](#left-join-left-outer-join)
   - [RIGHT JOIN](#right-join-right-outer-join)
   - [FULL JOIN](#full-join-full-outer-join)
   - [CROSS JOIN](#cross-join)
   - [SELF JOIN](#self-join)
6. [Aggregate Functions](#aggregate-functions)
   - [Basic Aggregates](#basic-aggregates)
   - [GROUP BY](#group-by)
   - [HAVING](#having-filter-on-aggregates)
7. [Subqueries](#subqueries)
   - [Subquery in WHERE](#subquery-in-where)
   - [Subquery in FROM](#subquery-in-from)
   - [Subquery in SELECT](#subquery-in-select)
   - [Correlated Subquery](#correlated-subquery)
8. [Advanced SQL Concepts](#advanced-sql-concepts)
   - [Common Table Expressions (CTE)](#common-table-expressions-cte)
   - [Recursive CTEs](#recursive-ctes)
   - [Window Functions](#window-functions)
   - [CASE Expression](#case-expression)
   - [PIVOT](#pivot-sql-server)
   - [String Functions](#string-functions)
   - [Date Functions](#date-functions)
9. [Transactions](#transactions)
10. [Database Management](#database-management)
    - [Indexes](#indexes)
    - [Views](#views)
    - [Stored Procedures](#stored-procedures-syntax-varies-by-database)
    - [Triggers](#triggers-syntax-varies-by-database)
11. [Performance Optimization Tips](#performance-optimization-tips)
12. [Database-Specific Differences](#database-specific-differences)
    - [MySQL](#mysql)
    - [PostgreSQL](#postgresql)
    - [SQL Server](#sql-server)
    - [Oracle](#oracle)

## Basic SQL Syntax

### SELECT Statement
```sql
-- Basic SELECT
SELECT column1, column2 FROM table_name;

-- Select all columns
SELECT * FROM table_name;

-- Select with aliases
SELECT column1 AS alias1, column2 AS alias2 FROM table_name;

-- Select distinct values
SELECT DISTINCT column1 FROM table_name;
```

### WHERE Clause
```sql
-- Basic filtering
SELECT * FROM table_name WHERE condition;

-- Common operators: =, <>, >, <, >=, <=
SELECT * FROM employees WHERE salary > 50000;

-- Multiple conditions
SELECT * FROM products WHERE price > 100 AND category = 'Electronics';
SELECT * FROM customers WHERE country = 'USA' OR country = 'Canada';

-- NOT operator
SELECT * FROM orders WHERE NOT status = 'Shipped';
```

### ORDER BY
```sql
-- Ascending order (default)
SELECT * FROM employees ORDER BY salary;

-- Descending order
SELECT * FROM employees ORDER BY salary DESC;

-- Multiple columns
SELECT * FROM employees ORDER BY department, hire_date DESC;
```

### LIMIT/OFFSET (pagination)
```sql
-- MySQL/PostgreSQL/SQLite
SELECT * FROM products LIMIT 10;
SELECT * FROM products LIMIT 10 OFFSET 20;

-- SQL Server
SELECT TOP 10 * FROM products;
SELECT * FROM products ORDER BY id OFFSET 20 ROWS FETCH NEXT 10 ROWS ONLY;

-- Oracle
SELECT * FROM products WHERE ROWNUM <= 10;
```

## Data Manipulation

### INSERT Statement
```sql
-- Insert a single row
INSERT INTO table_name (column1, column2) VALUES (value1, value2);

-- Insert multiple rows
INSERT INTO table_name (column1, column2) 
VALUES (value1, value2), (value3, value4), (value5, value6);

-- Insert from another table
INSERT INTO table_name (column1, column2)
SELECT column1, column2 FROM other_table WHERE condition;
```

### UPDATE Statement
```sql
-- Update all rows
UPDATE table_name SET column1 = value1, column2 = value2;

-- Update with condition
UPDATE table_name SET column1 = value1 WHERE condition;

-- Update with subquery
UPDATE table_name SET column1 = (SELECT column1 FROM other_table WHERE condition)
WHERE condition;
```

### DELETE Statement
```sql
-- Delete all rows
DELETE FROM table_name;

-- Delete with condition
DELETE FROM table_name WHERE condition;

-- Delete with subquery
DELETE FROM table_name WHERE column_name IN (SELECT column_name FROM other_table WHERE condition);
```

## Data Definition

### CREATE TABLE
```sql
CREATE TABLE table_name (
    column1 datatype constraints,
    column2 datatype constraints,
    ...
    PRIMARY KEY (column_name),
    FOREIGN KEY (column_name) REFERENCES other_table(column_name)
);

-- Example
CREATE TABLE employees (
    employee_id INT PRIMARY KEY,
    first_name VARCHAR(50) NOT NULL,
    last_name VARCHAR(50) NOT NULL,
    email VARCHAR(100) UNIQUE,
    hire_date DATE DEFAULT CURRENT_DATE,
    salary DECIMAL(10,2),
    department_id INT,
    FOREIGN KEY (department_id) REFERENCES departments(department_id)
);
```

### ALTER TABLE
```sql
-- Add column
ALTER TABLE table_name ADD column_name datatype constraints;

-- Modify column
ALTER TABLE table_name MODIFY column_name new_datatype new_constraints;
-- Or for some databases:
ALTER TABLE table_name ALTER COLUMN column_name TYPE new_datatype;

-- Drop column
ALTER TABLE table_name DROP COLUMN column_name;

-- Add constraint
ALTER TABLE table_name ADD CONSTRAINT constraint_name constraint_definition;

-- Drop constraint
ALTER TABLE table_name DROP CONSTRAINT constraint_name;
```

### DROP TABLE
```sql
-- Drop table
DROP TABLE table_name;

-- Drop if exists (safer)
DROP TABLE IF EXISTS table_name;
```

## Common Data Types

### Numeric Types
- `INT` or `INTEGER`: Standard integer
- `SMALLINT`: Small-range integer
- `BIGINT`: Large-range integer
- `DECIMAL(p,s)` or `NUMERIC(p,s)`: Exact decimal numbers (p=precision, s=scale)
- `FLOAT` or `REAL`: Approximate floating-point numbers
- `DOUBLE PRECISION`: Double precision floating-point numbers

### String Types
- `CHAR(n)`: Fixed-length character string
- `VARCHAR(n)`: Variable-length character string
- `TEXT`: Variable-length character string (unlimited length)
- `NCHAR/NVARCHAR`: Unicode character types

### Date/Time Types
- `DATE`: Date (YYYY-MM-DD)
- `TIME`: Time (HH:MM:SS)
- `DATETIME` or `TIMESTAMP`: Date and time
- `INTERVAL`: Time period

### Other Types
- `BOOLEAN`: True/False values
- `BLOB` or `BINARY`: Binary data
- `JSON`: JSON data (in supporting databases)
- `ARRAY`: Array of values (in supporting databases)
- `UUID`: Universally unique identifier

## Table Relationships and Joins

### INNER JOIN
```sql
SELECT a.column1, b.column2
FROM table_a a
INNER JOIN table_b b
ON a.common_column = b.common_column;
```

### LEFT JOIN (LEFT OUTER JOIN)
```sql
SELECT a.column1, b.column2
FROM table_a a
LEFT JOIN table_b b
ON a.common_column = b.common_column;
```

### RIGHT JOIN (RIGHT OUTER JOIN)
```sql
SELECT a.column1, b.column2
FROM table_a a
RIGHT JOIN table_b b
ON a.common_column = b.common_column;
```

### FULL JOIN (FULL OUTER JOIN)
```sql
SELECT a.column1, b.column2
FROM table_a a
FULL JOIN table_b b
ON a.common_column = b.common_column;
```

### CROSS JOIN
```sql
SELECT a.column1, b.column2
FROM table_a a
CROSS JOIN table_b b;
```

### SELF JOIN
```sql
SELECT a.column1, b.column2
FROM table_name a
JOIN table_name b
ON a.some_column = b.other_column;
```

## Aggregate Functions

### Basic Aggregates
```sql
-- COUNT
SELECT COUNT(*) FROM table_name;
SELECT COUNT(column_name) FROM table_name;
SELECT COUNT(DISTINCT column_name) FROM table_name;

-- SUM
SELECT SUM(column_name) FROM table_name;

-- AVG
SELECT AVG(column_name) FROM table_name;

-- MIN/MAX
SELECT MIN(column_name), MAX(column_name) FROM table_name;
```

### GROUP BY
```sql
SELECT column1, COUNT(*), SUM(column2)
FROM table_name
GROUP BY column1;
```

### HAVING (filter on aggregates)
```sql
SELECT column1, COUNT(*)
FROM table_name
GROUP BY column1
HAVING COUNT(*) > 5;
```

## Subqueries

### Subquery in WHERE
```sql
SELECT column1
FROM table_name
WHERE column2 IN (SELECT column2 FROM other_table WHERE condition);
```

### Subquery in FROM
```sql
SELECT a.column1
FROM (SELECT column1, column2 FROM table_name WHERE condition) a
WHERE a.column2 = value;
```

### Subquery in SELECT
```sql
SELECT column1,
       (SELECT AVG(column2) FROM other_table WHERE other_table.id = table_name.id) as avg_value
FROM table_name;
```

### Correlated Subquery
```sql
SELECT column1
FROM table_name t1
WHERE column2 > (SELECT AVG(column2) FROM table_name t2 WHERE t2.group = t1.group);
```

## Advanced SQL Concepts

### Common Table Expressions (CTE)
```sql
WITH cte_name AS (
    SELECT column1, column2
    FROM table_name
    WHERE condition
)
SELECT * FROM cte_name WHERE column1 > value;

-- Multiple CTEs
WITH cte1 AS (
    SELECT * FROM table1 WHERE condition1
),
cte2 AS (
    SELECT * FROM table2 WHERE condition2
)
SELECT * FROM cte1 JOIN cte2 ON cte1.id = cte2.id;
```

### Recursive CTEs
```sql
WITH RECURSIVE cte_name AS (
    -- Base case
    SELECT column1, column2 FROM table_name WHERE condition
    
    UNION ALL
    
    -- Recursive case
    SELECT t.column1, t.column2
    FROM table_name t
    JOIN cte_name c ON t.parent_id = c.id
)
SELECT * FROM cte_name;
```

### Window Functions
```sql
-- ROW_NUMBER
SELECT column1, 
       ROW_NUMBER() OVER (ORDER BY column2) as row_num
FROM table_name;

-- RANK and DENSE_RANK
SELECT column1,
       RANK() OVER (PARTITION BY column2 ORDER BY column3 DESC) as rank,
       DENSE_RANK() OVER (PARTITION BY column2 ORDER BY column3 DESC) as dense_rank
FROM table_name;

-- LEAD and LAG
SELECT column1, column2,
       LEAD(column2, 1) OVER (ORDER BY column1) as next_value,
       LAG(column2, 1) OVER (ORDER BY column1) as prev_value
FROM table_name;

-- FIRST_VALUE and LAST_VALUE
SELECT column1,
       FIRST_VALUE(column2) OVER (PARTITION BY column3 ORDER BY column1) as first_val,
       LAST_VALUE(column2) OVER (PARTITION BY column3 ORDER BY column1 
                                ROWS BETWEEN UNBOUNDED PRECEDING AND UNBOUNDED FOLLOWING) as last_val
FROM table_name;

-- Moving averages
SELECT column1, column2,
       AVG(column2) OVER (ORDER BY column1 ROWS BETWEEN 2 PRECEDING AND CURRENT ROW) as moving_avg
FROM table_name;
```

### CASE Expression
```sql
-- Simple CASE
SELECT column1,
       CASE column2
           WHEN 'value1' THEN 'result1'
           WHEN 'value2' THEN 'result2'
           ELSE 'default_result'
       END as case_result
FROM table_name;

-- Searched CASE
SELECT column1,
       CASE
           WHEN column2 > 100 THEN 'High'
           WHEN column2 > 50 THEN 'Medium'
           ELSE 'Low'
       END as category
FROM table_name;
```

### PIVOT (SQL Server)
```sql
SELECT *
FROM (SELECT category, month, sales FROM sales_data) as source_table
PIVOT (
    SUM(sales)
    FOR month IN ([Jan], [Feb], [Mar], [Apr])
) as pivot_table;
```

### String Functions
```sql
-- Concatenation
SELECT CONCAT(first_name, ' ', last_name) as full_name FROM employees;
-- Some databases use || for concatenation
SELECT first_name || ' ' || last_name as full_name FROM employees;

-- Substring
SELECT SUBSTRING(column_name, start, length) FROM table_name;
-- Or in Oracle:
SELECT SUBSTR(column_name, start, length) FROM table_name;

-- Upper/Lower case
SELECT UPPER(column_name), LOWER(column_name) FROM table_name;

-- Replace
SELECT REPLACE(column_name, 'find_string', 'replace_string') FROM table_name;

-- Trim
SELECT TRIM(column_name) FROM table_name;
SELECT LTRIM(column_name) FROM table_name;
SELECT RTRIM(column_name) FROM table_name;
```

### Date Functions
```sql
-- Current date/time
SELECT CURRENT_DATE, CURRENT_TIME, CURRENT_TIMESTAMP;

-- Extract parts
SELECT EXTRACT(YEAR FROM date_column) FROM table_name;
SELECT EXTRACT(MONTH FROM date_column) FROM table_name;
SELECT EXTRACT(DAY FROM date_column) FROM table_name;

-- Date arithmetic
SELECT date_column + INTERVAL '1 day' FROM table_name;
SELECT date_column + INTERVAL '1 month' FROM table_name;
SELECT date_column + INTERVAL '1 year' FROM table_name;

-- Date difference
SELECT DATEDIFF(date_column1, date_column2) FROM table_name;
-- Or in PostgreSQL:
SELECT date_column1 - date_column2 FROM table_name;

-- Format date
SELECT TO_CHAR(date_column, 'YYYY-MM-DD') FROM table_name;
```

## Transactions
```sql
-- Begin transaction
BEGIN TRANSACTION;
-- Or:
START TRANSACTION;

-- SQL statements...

-- Commit transaction
COMMIT;

-- Rollback transaction
ROLLBACK;

-- Savepoints
SAVEPOINT savepoint_name;
-- More SQL statements...
ROLLBACK TO savepoint_name;
```

## Database Management

### Indexes
```sql
-- Create index
CREATE INDEX index_name ON table_name (column_name);

-- Create unique index
CREATE UNIQUE INDEX index_name ON table_name (column_name);

-- Create composite index
CREATE INDEX index_name ON table_name (column1, column2);

-- Drop index
DROP INDEX index_name;
```

### Views
```sql
-- Create view
CREATE VIEW view_name AS
SELECT column1, column2
FROM table_name
WHERE condition;

-- Create or replace view
CREATE OR REPLACE VIEW view_name AS
SELECT column1, column2
FROM table_name
WHERE condition;

-- Drop view
DROP VIEW view_name;
```

### Stored Procedures (syntax varies by database)
```sql
-- MySQL
DELIMITER //
CREATE PROCEDURE procedure_name(param1 TYPE, param2 TYPE)
BEGIN
    -- SQL statements
END //
DELIMITER ;

-- SQL Server
CREATE PROCEDURE procedure_name
    @param1 TYPE,
    @param2 TYPE
AS
BEGIN
    -- SQL statements
END;
```

### Triggers (syntax varies by database)
```sql
-- MySQL
CREATE TRIGGER trigger_name
BEFORE INSERT ON table_name
FOR EACH ROW
BEGIN
    -- SQL statements
END;

-- PostgreSQL
CREATE TRIGGER trigger_name
BEFORE INSERT ON table_name
FOR EACH ROW
EXECUTE FUNCTION function_name();
```

## Performance Optimization Tips

1. **Use indexes wisely** - Create indexes on columns used in WHERE, JOIN, ORDER BY, and GROUP BY clauses
2. **Write efficient queries:**
   - Select only needed columns (avoid SELECT *)
   - Use LIMIT/TOP to restrict result sets
   - Use EXISTS instead of IN for large subqueries
   - Avoid functions in WHERE clauses
3. **Use EXPLAIN or EXPLAIN PLAN** to analyze query execution plans
4. **Optimize JOIN operations:**
   - Join on indexed columns
   - Use the smaller table as the driving table when possible
5. **Avoid correlated subqueries** when possible
6. **Consider materialized views** for complex, frequently run queries
7. **Use query hints** when necessary (database-specific)
8. **Partition large tables** by date or other logical divisions
9. **Use appropriate data types** - smaller is usually better
10. **Regular database maintenance:**
    - Update statistics
    - Rebuild indexes
    - Monitor query performance

## Database-Specific Differences

### MySQL
- Uses backticks (`) for identifiers
- LIMIT for pagination
- NOW() for current timestamp
- Supports stored procedures with DELIMITER

### PostgreSQL
- Case-sensitive identifiers
- Rich support for JSON data types
- Strong array and range type support
- Uses OFFSET/LIMIT for pagination

### SQL Server
- Uses square brackets [] for identifiers
- TOP instead of LIMIT
- Strong support for window functions
- GETDATE() for current timestamp

### Oracle
- Uses ROWNUM for pagination (or ROW_NUMBER() in newer versions)
- DUAL table for queries not tied to a table
- Strong support for hierarchical queries with CONNECT BY
- SYSDATE for current timestamp