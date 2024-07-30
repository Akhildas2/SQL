# JOINs

SQL JOINs are used to combine rows from two or more tables based on a related column between them. There are several types of JOINs, each serving a different purpose:

## 1. INNER JOIN

The `INNER JOIN` keyword selects records that have matching values in both tables.

### Syntax:

```sql
SELECT columns
FROM table1
INNER JOIN table2
ON table1.column = table2.column;
```

### Example:

```sql
SELECT person.first_name, car.make, car.model, car.price
FROM person
INNER JOIN car
ON person.car_id = car.id;
```

## 2. LEFT JOIN (or LEFT OUTER JOIN)

The `LEFT JOIN` keyword returns all records from the left table, and the matched records from the right table. The result is NULL from the right side if there is no match.

### Syntax:

```sql
SELECT columns
FROM table1
LEFT JOIN table2
ON table1.column = table2.column;
```

### Example:

```sql
SELECT person.first_name, car.make, car.model, car.price FROM person LEFT JOIN car ON person.car_id = car.id;
```

## 3. RIGHT JOIN (or RIGHT OUTER JOIN)

The `RIGHT JOIN` keyword returns all records from the right table, and the matched records from the left table. The result is NULL from the left side when there is no match.

### Syntax:

```sql
SELECT columns
FROM table1
RIGHT JOIN table2
ON table1.column = table2.column;
```

### Example:

```sql
SELECT person.first_name, car.make, car.model, car.price FROM person RIGHT JOIN car ON person.car_id = car.id;
```

## 4. FULL JOIN (or FULL OUTER JOIN)

The `FULL JOIN` keyword returns all records when there is a match in either left or right table. It returns NULLs where there is no match.

### Syntax:

```sql
SELECT columns
FROM table1
FULL JOIN table2
ON table1.column = table2.column;
```

### Example:

```sql
SELECT person.first_name, car.make, car.model, car.price FROM person FULL JOIN car ON person.car_id = car.id;
```

## 5. CROSS JOIN

The `CROSS JOIN` keyword returns the Cartesian product of the two tables. This means it returns all possible combinations of rows from both tables.

### Syntax:

```sql
SELECT columns
FROM table1
CROSS JOIN table2;
```

### Example:

```sql
SELECT person.first_name, car.make, car.model, car.price
FROM person
CROSS JOIN car;
```

## 6. SELF JOIN

A `SELF JOIN` is a regular join but the table is joined with itself.

### Syntax:

```sql
SELECT a.column1, b.column2
FROM table a
JOIN table b
ON a.common_column = b.common_column;
```

### Example:

```sql
SELECT p1.first_name AS person_name, p1.country_of_birth, p2.first_name AS fellow_countryman_name
FROM person p1
JOIN person p2
ON p1.country_of_birth = p2.country_of_birth
AND p1.id != p2.id
ORDER BY p1.country_of_birth, p1.first_name, p2.first_name;
```
