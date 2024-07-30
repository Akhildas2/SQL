# Operators

## Arithmetic Operators

- `+`: Add
- `-`: Subtract
- `*`: Multiply
- `/`: Divide
- `%`: Modulo

## Bitwise Operators

- `&`: Bitwise AND
- `|`: Bitwise OR
- `^`: Bitwise Exclusive OR

## Comparison Operators

- `=`: Equal To
- `>`: Greater Than
- `<`: Less Than
- `>=`: Greater Than or Equal To
- `<=`: Less Than or Equal To
- `<>`: Not Equal To (alternative: `!=`)

## Logical Operators

- `AND`: Logical AND
- `OR`: Logical OR
- `NOT`: Logical NOT

# Wildcards and LIKE Operator

## Wildcards

- `_`: Matches exactly one character.
- `%`: Matches zero or more characters.

Wildcards are commonly used along with the `LIKE` operator.

## `LIKE` Operator

The `LIKE` operator is used to search for a specified pattern in data.

Examples:

```sql
SELECT * FROM person WHERE email LIKE 'faiz@gmail.com';
SELECT * FROM person WHERE email LIKE '%@gmail.com'; -- returns every email ending with @gmail.com
SELECT * FROM person WHERE name LIKE 'F___'; -- returns 4-letter names starting with F
SELECT * FROM person WHERE name LIKE 'F_I%'; -- returns names with first letter F and third letter I
```

`LIKE` is case-sensitive. Use `ILIKE` for case-insensitive searches.

## `GROUP BY`

The `GROUP BY` statement is used to arrange identical data into groups. This is often used with aggregate functions (such as COUNT, MAX, MIN, SUM, AVG) to perform operations on each group of data.

Examples:

```sql
SELECT country, COUNT(*) FROM person GROUP BY country;
SELECT country, COUNT(*) FROM person GROUP BY country ORDER BY country;
SELECT country, COUNT(*) FROM person GROUP BY country ORDER BY COUNT(*);
```

## `HAVING `

The `HAVING` clause was added to SQL because the `WHERE` keyword could not be used with aggregate functions. It is used to filter records that work on summarized `GROUP BY` results.

Examples:

```sql
SELECT country, COUNT(*) FROM person GROUP BY country HAVING COUNT(*) > 5 ORDER BY country;
```

## `ORDER BY `

The `ORDER BY` clause is used to sort the result-set in ascending or descending order. By default, it sorts the records in ascending order. To sort the records in descending order, you can use the `DESC` keyword.

Examples:

```sql
SELECT * FROM person ORDER BY last_name;
SELECT * FROM person ORDER BY last_name DESC, first_name ASC;
```

# Set Operations

SQL set operators enable the comparison of rows from multiple tables or a combination of results from multiple queries. There are mainly four set operators:

## `UNION`

The `UNION` operator is used to combine the result sets of two or more `SELECT` statements. Each `SELECT` statement within `UNION` must have the same number of columns and the same data types, and the columns must be in the same order.

Example:

```sql
SELECT * FROM test UNION SELECT * FROM test2;
```

`UNION` only selects distinct values (no duplicates).

## `UNION ALL`

This operator allows duplicate values.

Example:

```sql
SELECT * FROM test UNION ALL SELECT * FROM test2;
```

## `INTERSECT`

The `INTERSECT` operator returns the result set that is common between two `SELECT` statements. The number of columns and data types must be the same in both queries.

Example:

```sql
SELECT * FROM table_name INTERSECT SELECT * FROM table_name_2;
```

## `MINUS`

The MINUS operator (also known as EXCEPT) returns the result set that is present in the first SELECT statement but not in the second SELECT statement. The number of columns and data types must be the same in both queries.
Example:

```sql
SELECT * FROM table_name EXCEPT SELECT * FROM table_name_2;
```
