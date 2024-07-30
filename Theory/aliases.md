# Aliases

An alias in SQL is a temporary name given to a table or a column for the duration of a query. Aliases are useful for making queries easier to read and write, especially when dealing with complex queries or when joining multiple tables. They are also handy for avoiding column name conflicts when performing joins or subqueries.

## Table Aliases

A table alias is used to rename a table in a query temporarily. It can help simplify your query, especially when dealing with long table names or multiple joins.

### Syntax:

```sql
SELECT column1, column2
FROM table_name AS alias_name
WHERE condition;
```

### Example

```sql
SELECT c.id, c.make, c.model,
       c.price AS original_price,
       ROUND(c.price * 0.10, 1) AS discount,
       ROUND(c.price - c.price * 0.10, 2) AS amount_after_discount
FROM car AS c;
```

## Column Aliases

A column alias is used to rename a column in the result set. This is useful for providing more meaningful column names in the output.

### Syntax:

```sql
SELECT column_name AS alias_name
FROM table_name
WHERE condition;
```

### Example

```sql
SELECT id, make, model,
       price AS original_price,
       ROUND(price * 0.10, 1) AS discount,
       ROUND(price - price * 0.10, 2) AS amount_after_discount
FROM car;
```
