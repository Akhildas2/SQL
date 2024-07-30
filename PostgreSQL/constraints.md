# SQL Constraints

Constraints in SQL are used to enforce rules on the data in a table. They ensure the accuracy and reliability of the data in a database. Here are the main types of constraints:

## 1. `PRIMARY KEY`

- **Definition**: Combines `NOT NULL` and `UNIQUE` constraints. Uniquely identifies each row in a table.

## 2. `FOREIGN  KEY`

- **Definition**: Maintains referential integrity by linking columns in different tables. Prevents actions that would break these links.

## 3. `UNIQUE`

- **Definition**: Ensures that all values in a column are distinct.
- **Syntax**:

  ```sql
  CREATE TABLE table_name (
    column_name data_type UNIQUE
  );
  ```

## 4. `NOT NULL`

- **Definition**: Ensures that a column cannot have a NULL value.

```sql
CREATE TABLE table_name (
   column_name data_type NOT NULL
);
```

## 5. `CHECK`

- **Definition**: Ensures that the values in a column meet a specific condition.

```sql
CREATE TABLE table_name (
   column_name data_type,
   CHECK (condition)
);
```

## 6. `DEFAULT`

- **Definition**: Provides a default value for a column if no value is specified.

```sql
CREATE TABLE table_name (
   column_name data_type DEFAULT default_value
);
```

### Example

```sql
CREATE TABLE employees (
    employee_id INT PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    department_id INT,
    salary DECIMAL(10, 2) CHECK (salary > 0),
    FOREIGN KEY (department_id) REFERENCES departments(department_id)
);
```
```sql
ALTER TABLE employees
ADD CONSTRAINT unique_employee_email UNIQUE (email);
ALTER TABLE person ADD CHECK (gender = 'female' OR gender = 'male');
```