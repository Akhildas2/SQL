# Keys

## 1. Primary Key

- **Definition**: A column (or a set of columns) in a table that uniquely identifies each row in that table.
- **Characteristics**:
  - Must contain unique values.
  - Cannot contain NULL values.
  - Each table should have only one primary key.
- **Syntax Example**:

  ```sql
  CREATE TABLE employees (
      employee_id INT PRIMARY KEY,
      first_name VARCHAR(50),
      last_name VARCHAR(50)
  );
  ```

## 2. Foreign Key

- **Definition**: A column (or a set of columns) in one table that refers to the primary key in another table.
- **Characteristics**:
  - Establishes and enforces a link between the data in the two tables.
  - Ensures referential integrity by restricting the values that can be entered in the foreign key column.
- **Syntax Example**:

  ```sql
  CREATE TABLE orders (
    order_id INT PRIMARY KEY,
    customer_id INT,
    FOREIGN KEY (customer_id) REFERENCES customers(customer_id)
  );
  ```

## 3. Unique Key

- **Definition**: A constraint that ensures all values in a column are unique, similar to a primary key, but a table can have multiple unique keys.
- **Characteristics**:
  - Allows NULL values unless specified otherwise.
  - Can be used to enforce uniqueness for columns that are not primary keys.
- **Syntax Example**:

  ```sql
  CREATE TABLE users (
    user_id INT PRIMARY KEY,
    email VARCHAR(100) UNIQUE
  );
  ```

  ## 4. Composite Key

- **Definition**: A primary key that consists of two or more columns to uniquely identify a row in a table.
- **Characteristics**:
  - Useful when a single column is not sufficient to uniquely identify a row.
  - Each column in the composite key must be non-null.
- **Syntax Example**:

  ```sql
  CREATE TABLE course_enrollments (
    student_id INT,
    course_id INT,
    enrollment_date DATE,
    PRIMARY KEY (student_id, course_id)
  );
  ```

  ## 5. Candidate Key

- **Definition**:A column or a set of columns that can uniquely identify a row in a table. Each table can have multiple candidate keys, but one of them is chosen as the primary key.
- **Characteristics**:
  - Each candidate key must be unique and not contain NULL values.
  - Candidate keys are potential primary keys.
- **Syntax Example**:

  ```sql
  CREATE TABLE products (
    product_id INT,
    sku VARCHAR(100) UNIQUE,
    name VARCHAR(100),
    PRIMARY KEY (product_id)
  );
  ```

  ## 6. Alternate Key

- **Definition**:A candidate key that is not chosen as the primary key.
- **Characteristics**:
  - Provides an alternate way to uniquely identify records in the table.
- **Syntax Example**:

  ```sql
  CREATE TABLE orders (
    order_id INT PRIMARY KEY,
    order_number VARCHAR(100) UNIQUE
  );
  ```

  ## 7. Super Key

- **Definition**: A set of one or more columns that can uniquely identify rows in a table. It may include additional columns that are not necessary for uniqueness.
- **Characteristics**:
  - Includes all candidate keys as subsets.
- **Syntax Example**:

  ```sql
  CREATE TABLE sales (
    sale_id INT,
    sale_date DATE,
    product_id INT,
    PRIMARY KEY (sale_id, sale_date)
  );

  ```

  ## 8. Unique Constraints

- **Definition**: Constraints that ensure the uniqueness of values in one or more columns, similar to unique keys.
- **Characteristics**:
  - Can be applied to enforce uniqueness on any column or combination of columns.
- **Syntax Example**:

  ```sql
  CREATE TABLE employees (
    employee_id SERIAL PRIMARY KEY,
    email VARCHAR(100),
    CONSTRAINT unique_email UNIQUE (email)
  );
  ```
