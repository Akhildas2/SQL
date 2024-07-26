# Basic Commands

## Basic PostgreSQL Commands for Connecting to `psql` on Windows

### Connecting to `psql`

- **Connect to `psql`:**

```sql
 psql -U postgres
```

Replace postgres with your PostgreSQL username.

- **Enter Password:**
  You will be prompted to enter your password after running the above command. Simply type your password (e.g., postgres) and press Enter.

- **Connect to a Database:**

  ```sql
  \c database_name
  ```

  Replace database_name with the name of your database.

### Useful Commands

- **List all databases:**

```sql
 \l
```

- **List all tables in the current database:**

  ```sql
  \d
  ```

- **Execute SQL commands from a file:**

```sql
 \i /path/to/sql/file.sql
```

Replace /path/to/sql/file.sql with the actual path to your SQL file.

## Database Basic Commands

### Creating a Database

```sql
CREATE DATABASE database_name;
```

Replace database_name with the name of the database you want to create.

### Deleting a Database

```sql
DROP DATABASE database_name;
```

Replace database_name with the name of the database you want to delete.

### Backup a Database

To back up a database, use the pg_dump utility from the command line:

sh

```sql
pg_dump -U username database_name > backup_file.sql
```

Replace username with your PostgreSQL username, database_name with the name of the database you want to back up, and backup_file.sql with the name of the backup file.

### Rename a Database

```sql
ALTER DATABASE old_database_name RENAME TO new_database_name;

```

Replace old_database_name with the current name of the database and new_database_name with the new name you want to give to the database.

## PostgreSQL Table Basics

### Creating a Table

```sql
CREATE TABLE employees (
    employee_id INT,
    first_name VARCHAR(50) ,
    last_name VARCHAR(50) ,
    email VARCHAR(100),
    hire_date DATE 
);
```

This command creates a new table named employees with columns.

### Deleting a Table

```sql
DROP TABLE employees;
```

This command deletes the employees table and all its data from the database.

### Renaming a Table

```sql
ALTER TABLE employees RENAME TO staff;
```

 This command renames the employees table to staff.

 ### Renaming a Table

```sql
ALTER TABLE employees RENAME TO staff;
```

 This command renames the employees table to staff.

 ### Creating a Table with Constraints

```sql
CREATE TABLE departments (
    department_id SERIAL PRIMARY KEY,
    department_name VARCHAR(50) NOT NULL,
    manager_id INT,
    CONSTRAINT fk_manager
        FOREIGN KEY(manager_id) 
        REFERENCES employees(employee_id)
);
```

This command creates a departments table with specified columns and a foreign key constraint.

 ### Inserting Data/Row

```sql
INSERT INTO employees (first_name, last_name, email, hire_date)
VALUES ('John', 'Doe', 'john.doe@example.com', '2023-01-15');
```

This command inserts a new row into the employees table.

 ### Deleting Data/Row

```sql
DELETE FROM employees
WHERE employee_id = 1;
```

This command deletes the row from the employees table where the employee_id is 1.

 ### Getting Data from SQL DB

```sql
SELECT first_name, last_name, email
FROM employees;
```

This command retrieves the first_name, last_name, and email columns from the employees table.

 ### Sorting

```sql
SELECT first_name, last_name, hire_date
FROM employees
ORDER BY hire_date DESC;
```

This command retrieves and sorts employees by their hire date in descending order.

 ### Filtering Duplicates

```sql
SELECT DISTINCT department_name
FROM departments;
```

This command retrieves unique department names from the departments table.

 ### Filtering

```sql
SELECT first_name, last_name, email
FROM employees
WHERE hire_date > '2023-01-01';
```

 This command retrieves rows from the employees table where the hire date is after January 1, 2023.

 ### Selecting String with Condition

```sql
SELECT first_name, last_name, email
FROM employees
WHERE email LIKE '%@example.com';
```

This command retrieves rows where the email ends with @example.com.

 ### Limiting the Number of Results

```sql
SELECT first_name, last_name, email
FROM employees
LIMIT 5;
```

This command limits the number of rows returned by the query to 5.

 ### Skipping Rows in the Results

```sql
SELECT first_name, last_name, email
FROM employees
OFFSET 10;
```

 This command skips the first 10 rows before returning results.

 ### IN

```sql
SELECT first_name, last_name, email
FROM employees
WHERE department_id IN (1, 2, 3);
```

This command retrieves rows where the department_id is either 1, 2, or 3.

 ### BETWEEN

```sql
SELECT first_name, last_name, email
FROM employees
WHERE hire_date BETWEEN '2023-01-01' AND '2023-12-31';
```

This command retrieves rows where the hire date is between January 1, 2023, and December 31, 2023.

### FETCH

```sql
SELECT first_name, last_name, email
FROM employees
LIMIT 5 OFFSET 10;
```

This command retrieves 5 rows, starting from the 11th row.

### Adding Columns to a Table

```sql
ALTER TABLE employees
ADD COLUMN phone_number VARCHAR(15);
```

This command adds a new column phone_number to the employees table.

### Deleting a Column from a Table

```sql
ALTER TABLE employees
DROP COLUMN phone_number;
```

This command deletes the phone_number column from the employees table.

### Renaming a Column

```sql
ALTER TABLE employees
RENAME COLUMN first_name TO given_name;
```

This command renames the first_name column to given_name in the employees table.