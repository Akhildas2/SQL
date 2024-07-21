# Types of SQL Commands

Developers use Structured Query Language (SQL) commands to interact with relational databases. SQL commands are categorized into five main types, each serving a specific purpose:

## 1. Data Definition Language (DDL)

DDL commands are used to define and manage the structure of database objects like tables, indexes, and schemas. These commands include:

- **CREATE:** Defines new tables, databases, or other database objects.
  ```sql
  CREATE TABLE table_name (
      column1 datatype constraints,
      column2 datatype constraints,
      ...
  );

```

- **ALTER:** Modifies the structure of an existing database object, such as adding or dropping columns.

```sql
ALTER TABLE table_name
ADD COLUMN column_name datatype;
```

- **DROP:**  Deletes existing tables, indexes, or other database objects.

```sql
DROP TABLE table_name;
```

## 2. Data Manipulation Language (DML)

DML commands are used to manipulate the data within database objects. They allow you to insert, update, delete, and retrieve data. These commands include:

- **INSERT:** Adds new rows to a table.

```sql
INSERT INTO table_name (column1, column2, ...)
VALUES (value1, value2, ...);
```

- **UPDATE:** Modifies existing data within a table based on a specified condition.

```sql
UPDATE table_name
SET column1 = value1, column2 = value2, ...
WHERE condition;
```

- **DELETE:** Removes rows from a table based on a specified condition.

```sql
DELETE FROM table_name
WHERE condition;
```

- **SELECT:** Retrieves data from one or more tables.

## 3. Data Query Language (DQL)

DQL commands are used specifically to query and retrieve data from the database. The primary command is:

- **SELECT:** Queries the database to retrieve data according to specified criteria. It is technically part of DML, but it’s often considered separately due to its significance in querying data.

```sql
SELECT column1, column2, ...
FROM table_name
WHERE condition
ORDER BY column1
LIMIT number;
```

## 4. Data Control Language (DCL)

DCL commands are used to control access to data within the database. They manage user permissions and security. These commands include:

- **GRANT:** Provides specific privileges to users or roles.

```sql
GRANT privilege_type
ON object
TO user;
```

- **REVOKE:** Removes specific privileges from users or roles.

```sql
REVOKE privilege_type
ON object
FROM user;
```

## 5. Transaction Control Language (TCL)

TCL commands manage the transactions in a database. They ensure data integrity by allowing you to commit or roll back changes. These commands include:

- **BEGIN:** Starts a new transaction.

```sql
BEGIN;
```

- **COMMIT:** Saves all changes made during the current transaction.

```sql
COMMIT;
```

- **ROLLBACK:** Reverts all changes made during the current transaction.

```sql
ROLLBACK;
```
