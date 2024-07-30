# Aggregation Functions

Aggregation functions in PostgreSQL perform a calculation on a set of values and return a single value. They are often used with the `GROUP BY` clause of the `SELECT` statement.

## Common Aggregation Functions

### 1. `COUNT()`

Counts the number of rows or non-NULL values.

```sql
-- Count all rows
SELECT COUNT(*) FROM table_name;

-- Count non-NULL values in a column
SELECT COUNT(column_name) FROM table_name;
```

### 2. `SUM()`

Calculates the sum of a set of numeric values.

```sql
SELECT SUM(column_name) FROM table_name;
--change colmn name and table name
```

### 3. `AVG()`

Calculates the average (mean) of a set of numeric values.

```sql
SELECT AVG(column_name) FROM table_name;
--change colmn name and table name
```

### 4. `MAX()`

Returns the maximum value in a set of values.

```sql
SELECT MAX(column_name) FROM table_name;
--change colmn name and table name

```

### 5. `MIN()`

Returns the minimum value in a set of values.

```sql
SELECT MIN(column_name) FROM table_name;
--change colmn name and table name
```

To avoid the decimal issue use `ROUND()`

### Examples

```sql
SELECT make, MIN(price) FROM car GROUP BY make;
SELECT make, MAX(price) FROM car GROUP BY make;
SELECT make, AVG(price) FROM car GROUP BY make;
SELECT make, COUNT(*) FROM car GROUP BY make;
SELECT SUM(price) FROM car;
```
