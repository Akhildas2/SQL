# Normalization

Normalization is a process in database design used to reduce data redundancy and improve data integrity. It involves organizing a database into tables and defining relationships between them.

## First Normal Form (1NF)

A table is in 1NF if:

- It contains only atomic (indivisible) values.
- Each column contains values of a single type.
- Each column must have a unique name.
- The order in which data is stored does not matter.

**Example:**

Before 1NF:

| StudentID | Name  | Courses       |
| --------- | ----- | ------------- |
| 1         | Alice | Math, Science |
| 2         | Bob   | Math, History |

After applying 1NF:

| StudentID | Name  | Course  |
| --------- | ----- | ------- |
| 1         | Alice | Math    |
| 1         | Alice | Science |
| 2         | Bob   | Math    |
| 2         | Bob   | History |

## Second Normal Form (2NF)

A table is in 2NF if:

- It is in 1NF.
- All non-key attributes are fully functionally dependent on the entire primary key.

**Example:**

Before 2NF:

| StudentID | Course  | Instructor |
| --------- | ------- | ---------- |
| 1         | Math    | Mr. Smith  |
| 1         | Science | Mrs. Jones |
| 2         | Math    | Mr. Smith  |
| 2         | History | Ms. Brown  |

After applying 2NF (split into two tables):

**StudentsCourses Table:**

| StudentID | Course  |
| --------- | ------- |
| 1         | Math    |
| 1         | Science |
| 2         | Math    |
| 2         | History |

**Courses Table:**

| Course  | Instructor |
| ------- | ---------- |
| Math    | Mr. Smith  |
| Science | Mrs. Jones |
| History | Ms. Brown  |

## Third Normal Form (3NF)

A table is in 3NF if:

- It is in 2NF.
- All the attributes are functionally dependent on the primary key and not on other non-key attributes (no `transitive dependency`).

**Example:**

Before 3NF:

| StudentID | Course  | Instructor | InstructorEmail   |
| --------- | ------- | ---------- | ----------------- |
| 1         | Math    | Mr. Smith  | smith@example.com |
| 1         | Science | Mrs. Jones | jones@example.com |
| 2         | Math    | Mr. Smith  | smith@example.com |
| 2         | History | Ms. Brown  | brown@example.com |

After applying 3NF (split into three tables):

**StudentsCourses Table:**

| StudentID | Course  |
| --------- | ------- |
| 1         | Math    |
| 1         | Science |
| 2         | Math    |
| 2         | History |

**Courses Table:**

| Course  | Instructor |
| ------- | ---------- |
| Math    | Mr. Smith  |
| Science | Mrs. Jones |
| History | Ms. Brown  |

**Instructors Table:**

| Instructor | InstructorEmail   |
| ---------- | ----------------- |
| Mr. Smith  | smith@example.com |
| Mrs. Jones | jones@example.com |
| Ms. Brown  | brown@example.com |

## Boyce-Codd Normal Form (BCNF)

A table is in BCNF if:

- It is in 3NF.
- Every determinant is a candidate key.

**Example:**

If a table has dependencies where non-key attributes are not fully functionally dependent on a candidate key, it needs to be decomposed to satisfy BCNF requirements.

## Fourth Normal Form (4NF)

A table is in 4NF if:

- It is in 3NF.
- It has no multi-valued dependencies (i.e., no attribute in a table should have multiple independent sets of values).

**Example:**

Consider a table with multi-valued dependencies:

| StudentID | Course  | Language |
| --------- | ------- | -------- |
| 1         | Math    | English  |
| 1         | Math    | French   |
| 1         | Science | English  |
| 1         | Science | Spanish  |

Here, "Language" and "Course" are independent. To achieve 4NF, decompose the table:

**StudentCourses Table:**

| StudentID | Course  |
| --------- | ------- |
| 1         | Math    |
| 1         | Science |

**StudentLanguages Table:**

| StudentID | Language |
| --------- | -------- |
| 1         | English  |
| 1         | French   |
| 1         | Spanish  |

## Fifth Normal Form (5NF)

A table is in 5NF if:

- It is in 4NF.
- It has no join dependency and cannot be further decomposed without losing information.

**Example:**

Consider a table with join dependencies:

| Course  | Instructor | Semester    |
| ------- | ---------- | ----------- |
| Math    | Mr. Smith  | Fall 2024   |
| Math    | Mrs. Jones | Spring 2025 |
| Science | Mr. Smith  | Fall 2024   |
| History | Ms. Brown  | Spring 2025 |

To achieve 5NF, decompose into:

**CoursesInstructors Table:**

| Course  | Instructor |
| ------- | ---------- |
| Math    | Mr. Smith  |
| Math    | Mrs. Jones |
| Science | Mr. Smith  |
| History | Ms. Brown  |

**CoursesSemesters Table:**

| Course  | Semester    |
| ------- | ----------- |
| Math    | Fall 2024   |
| Math    | Spring 2025 |
| Science | Fall 2024   |
| History | Spring 2025 |

**InstructorsSemesters Table:**

| Instructor | Semester    |
| ---------- | ----------- |
| Mr. Smith  | Fall 2024   |
| Mrs. Jones | Spring 2025 |
| Ms. Brown  | Spring 2025 |

---

Normalization helps maintain a clean and efficient database design, addressing various types of redundancy and dependency issues. Each normal form addresses specific issues to ensure data integrity and reduce redundancy.

## Advantages

1. **Reduced Redundancy**
   - Eliminates duplicate data, saving storage and ensuring consistency.

2. **Improved Data Integrity**
   - Minimizes data anomalies and errors.

3. **Easier Maintenance**
   - Simplifies updates and changes by centralizing data.

4. **Improved Query Performance (in some cases)**
   - Can make queries more efficient by reducing data volume.

5. **Enhanced Flexibility**
   - Adapts more easily to changes in data requirements.

## Disadvantages

1. **Increased Complexity**
   - Makes the database schema more complex and harder to understand.

2. **Potential Performance Overhead**
   - Joins between multiple tables can slow down queries.

3. **Increased Development Time**
   - Requires more time to design and implement.

4. **Complex Data Retrieval**
   - Queries can become more complex and harder to optimize.

5. **Storage Overhead**
   - May require more storage due to additional tables and indices.