# Handling NULL Values

## NULL

In SQL, `NULL` represents the absence of a value. It is not the same as an empty string or a zero; rather, it indicates that a value is missing or unknown.

### Key Points:

- **NULL is not equal to NULL**: You cannot use the equality operator (`=`) to compare NULL values. Instead, use `IS NULL` or `IS NOT NULL`.
- **Handling NULL in expressions**: Any arithmetic operation or function involving NULL generally results in NULL. For instance, `NULL + 5` is `NULL`.
- **NULL in aggregate functions**: Functions like `COUNT()`, `SUM()`, `AVG()`, etc., typically ignore NULL values. For example, `SUM(column)` will only sum non-NULL values.

### Example:

```sql
SELECT *
FROM employees
WHERE manager_id IS NULL;
```

This query retrieves all employees who do not have a manager (manager_id is NULL).

## COALESCE

The `COALESCE` function returns the first non-NULL value in a list of arguments. It is useful for providing default values in queries.

### Key Points:

- If all arguments are NULL, `COALESCE` returns NULL.
- `COALESCE` is commonly used to provide default values where NULLs might be present.

### syntax:

```sql
COALESCE(expression1, expression2, ..., expressionN)
```

expression1, expression2, ..., expressionN: A list of expressions to be evaluated in order. The function returns the first non-NULL value from this list.

### Example:

```sql
SELECT COALESCE(email, 'No Email Provided') FROM person;
```
