# PostgreSQL Cheatsheet

## Database Connection & Management

### Connect to PostgreSQL
```bash
# Connect to default database
psql

# Connect to specific database
psql -d database_name

# Connect with user
psql -U username -d database_names

# Connect to remote server
psql -h hostname -U username -d database_name
```

### Database Operations
```sql
-- Create a database
CREATE DATABASE database_name;

-- List all databases
\l

-- Switch to another database
\c database_name

-- Drop (delete) a database
DROP DATABASE database_name;

-- Rename a database
ALTER DATABASE database_name RENAME TO new_database_name;
```


## Useful psql Commands

```
\? - Show psql command help
\h - SQL command help
\l - List databases
\c dbname - Connect to a database
\dt - List tables
\d table_name - Describe a table
\du - List users and roles
\dn - List schemas
\df - List functions
\dv - List views
\timing - Toggle timing of commands
\e - Open editor
\q - Quit psql
```

## Users and Permissions

```sql
-- Create user
CREATE USER username WITH PASSWORD 'password';

-- Create role
CREATE ROLE role_name;

-- Grant privileges
GRANT privilege ON table_name TO username;

-- Common privileges: SELECT, INSERT, UPDATE, DELETE, TRUNCATE, REFERENCES, TRIGGER, CREATE, CONNECT, TEMPORARY, EXECUTE, USAGE

-- Grant all privileges
GRANT ALL PRIVILEGES ON DATABASE database_name TO username;

-- Revoke privileges
REVOKE privilege ON table_name FROM username;

-- Alter user password
ALTER USER username WITH PASSWORD 'new_password';

-- Drop user
DROP USER username;
```


⚠️ You cannot drop a user if they own any databases, tables, or other objects. In that case, you'll need to reassign or drop those objects first.

Example to reassign and drop owned objects:

```sql
REASSIGN OWNED BY username TO postgres;
DROP OWNED BY username;
DROP USER username;
```

## Backup and Restore

```bash
# Backup a database
pg_dump dbname > backup_file.sql

# Backup with compression
pg_dump dbname | gzip > backup_file.gz

# Restore a database
psql dbname < backup_file.sql

# Restore a compressed backup
gunzip -c backup_file.gz | psql dbname
```


## Table Operations

### Create Tables
```sql
-- Create a basic table
CREATE TABLE table_name (
    column1 datatype1 constraints,
    column2 datatype2 constraints,
    ...
);

-- Example: Create users table
CREATE TABLE users (
    id SERIAL PRIMARY KEY,
    username VARCHAR(50) UNIQUE NOT NULL,
    email VARCHAR(100) UNIQUE NOT NULL,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

### Common Data Types
- `INTEGER`, `INT` - whole numbers
- `SERIAL` - auto-incrementing integer
- `NUMERIC`, `DECIMAL` - exact decimal numbers
- `VARCHAR(n)` - variable-length string with limit
- `TEXT` - unlimited-length text
- `BOOLEAN` - true/false values
- `DATE` - date (no time)
- `TIME` - time (no date)
- `TIMESTAMP` - date and time
- `JSON`, `JSONB` - JSON data

### Modify Tables
```sql
-- Add a column
ALTER TABLE table_name ADD COLUMN column_name datatype constraints;

-- Drop a column
ALTER TABLE table_name DROP COLUMN column_name;

-- Rename a column
ALTER TABLE table_name RENAME COLUMN old_name TO new_name;

-- Change column data type
ALTER TABLE table_name ALTER COLUMN column_name TYPE new_datatype;

-- Add constraints
ALTER TABLE table_name ADD CONSTRAINT constraint_name constraint_definition;

-- Example: Add foreign key
ALTER TABLE orders ADD CONSTRAINT fk_customer FOREIGN KEY (customer_id) REFERENCES customers(id);

-- Remove a table
DROP TABLE table_name;

-- List all tables
\dt
```

## Data Manipulation

### Insert Data
```sql
-- Insert a single row
INSERT INTO table_name (column1, column2, ...) VALUES (value1, value2, ...);

-- Insert multiple rows
INSERT INTO table_name (column1, column2, ...)
VALUES 
    (value1, value2, ...),
    (value1, value2, ...);

-- Insert with returning clause
INSERT INTO table_name (column1) VALUES ('value') RETURNING id, column1;
```

### Query Data
```sql
-- Select all columns
SELECT * FROM table_name;

-- Select specific columns
SELECT column1, column2 FROM table_name;

-- Select with conditions
SELECT * FROM table_name WHERE condition;

-- Order results
SELECT * FROM table_name ORDER BY column_name ASC|DESC;

-- Limit results
SELECT * FROM table_name LIMIT 10;

-- Skip rows
SELECT * FROM table_name OFFSET 10;

-- Count results
SELECT COUNT(*) FROM table_name;

-- Group results
SELECT column1, COUNT(*) FROM table_name GROUP BY column1;

-- Filter groups
SELECT column1, COUNT(*) FROM table_name GROUP BY column1 HAVING COUNT(*) > 5;
```

### Update Data
```sql
-- Update rows
UPDATE table_name SET column1 = value1 WHERE condition;

-- Update multiple columns
UPDATE table_name SET column1 = value1, column2 = value2 WHERE condition;

-- Update all rows
UPDATE table_name SET column1 = value1;

-- Update with returning clause
UPDATE table_name SET column1 = value1 WHERE condition RETURNING *;
```

### Delete Data
```sql
-- Delete rows
DELETE FROM table_name WHERE condition;

-- Delete all rows
DELETE FROM table_name;

-- Delete with returning clause
DELETE FROM table_name WHERE condition RETURNING *;
```

## Joins

```sql
-- Inner join
SELECT t1.column1, t2.column2
FROM table1 t1
INNER JOIN table2 t2 ON t1.id = t2.table1_id;

-- Left join
SELECT t1.column1, t2.column2
FROM table1 t1
LEFT JOIN table2 t2 ON t1.id = t2.table1_id;

-- Right join
SELECT t1.column1, t2.column2
FROM table1 t1
RIGHT JOIN table2 t2 ON t1.id = t2.table1_id;

-- Full outer join
SELECT t1.column1, t2.column2
FROM table1 t1
FULL OUTER JOIN table2 t2 ON t1.id = t2.table1_id;
```

## Indexes

```sql
-- Create index
CREATE INDEX index_name ON table_name (column_name);

-- Create unique index
CREATE UNIQUE INDEX index_name ON table_name (column_name);

-- Create composite index
CREATE INDEX index_name ON table_name (column1, column2);

-- Drop index
DROP INDEX index_name;

-- List indexes
\di
```

## Transactions

```sql
-- Begin a transaction
BEGIN;

-- Commit a transaction
COMMIT;

-- Rollback a transaction
ROLLBACK;

-- Create a savepoint
SAVEPOINT savepoint_name;

-- Rollback to a savepoint
ROLLBACK TO savepoint_name;
```

