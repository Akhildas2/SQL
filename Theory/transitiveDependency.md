# Transitive Dependency

A transitive dependency occurs in a relational database when a non-key attribute depends on another non-key attribute rather than directly on the primary key. This type of dependency can lead to data redundancy and anomalies.

## Understanding Transitive Dependency

In a relational database table, if you have a functional dependency where:

- **A → B** (A determines B), and
- **B → C** (B determines C),

then **C** is transitively dependent on **A** through **B**. This means that **C** depends on **B**, and **B** depends on **A**, making **C** indirectly dependent on **A**.

## Example

Consider the following table:

| EmployeeID | EmployeeName | Department | DepartmentHead |
| ---------- | ------------ | ---------- | -------------- |
| 1          | Alice        | HR         | John Doe       |
| 2          | Bob          | IT         | Jane Smith     |
| 3          | Charlie      | HR         | John Doe       |

Here:

- `EmployeeID` is the primary key.
- `Department` is functionally dependent on `EmployeeID` (`EmployeeID → Department`).
- `DepartmentHead` is functionally dependent on `Department` (`Department → DepartmentHead`).

This creates a transitive dependency:

- `EmployeeID → Department`
- `Department → DepartmentHead`
- Therefore, `EmployeeID → DepartmentHead` (through Department).

## Decomposition to Remove Transitive Dependency

To achieve Third Normal Form (3NF), which removes transitive dependencies, you decompose the table into separate tables where non-key attributes depend only on the primary key.

**Original Table:**

| EmployeeID | EmployeeName | Department | DepartmentHead |
| ---------- | ------------ | ---------- | -------------- |
| 1          | Alice        | HR         | John Doe       |
| 2          | Bob          | IT         | Jane Smith     |
| 3          | Charlie      | HR         | John Doe       |

**Decomposed Tables:**

**Employees Table:**

| EmployeeID | EmployeeName | Department |
| ---------- | ------------ | ---------- |
| 1          | Alice        | HR         |
| 2          | Bob          | IT         |
| 3          | Charlie      | HR         |

**Departments Table:**

| Department | DepartmentHead |
| ---------- | -------------- |
| HR         | John Doe       |
| IT         | Jane Smith     |

In this decomposition:

- The `Employees` table has a primary key `EmployeeID`, and `Department` directly depends on `EmployeeID`.
- The `Departments` table has a primary key `Department`, and `DepartmentHead` depends on `Department`.

By separating the concerns, you eliminate the transitive dependency and reduce redundancy. Each non-key attribute is now directly dependent on the primary key of its respective table.

## Benefits of Removing Transitive Dependencies

- **Reduced Redundancy:** Avoids repeating information, thus saving storage space and ensuring data consistency.
- **Improved Data Integrity:** Changes to data are easier to manage and less prone to errors.
- **Easier Maintenance:** Simplifies updates, deletions, and insertions in the database, making the schema easier to manage.

Normalization, including the removal of transitive dependencies, helps maintain a clean and efficient database design, addressing various types of redundancy and dependency issues.
