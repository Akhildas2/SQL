# Views

A **view** in SQL is a virtual table based on the result of an SQL query. It does not store data itself but displays data from one or more tables. Views can simplify complex queries, provide a layer of security, and encapsulate logic.

## Key Points

1. **Definition**:

   - A view is created using the `CREATE VIEW` statement.
   - It can include data from one or more tables and can also use complex queries.

2. **Syntax**:

   ```sql
   CREATE VIEW view_name AS
   SELECT column1, column2, ...
   FROM table_name
   WHERE condition;
   ```

3. **Advantages**:

   1. **Simplifies Complex Queries**:

   - Views encapsulate complex queries, making them easier to work with and manage. This can be particularly useful for simplifying repetitive queries.

   2. **Security**:

   - Views can restrict access to sensitive data by displaying only specific columns or rows. Users can be given access to a view without giving them access to the underlying tables.

   3. **Data Abstraction**:

   - Views provide an abstracted way to interact with the data without exposing the underlying table structures. This can help in maintaining a stable interface for querying even if the underlying database schema changes.

   4. **Encapsulation of Business Logic**:

   - Business logic can be encapsulated within views. For example, calculations or transformations that need to be applied to the data can be handled in a view, ensuring consistency across different queries.

   5. **Data Aggregation**:

   - Views can aggregate data from multiple tables, performing operations such as summing, averaging, or counting. This is useful for reporting and analytical purposes.

   6. **Simplified Data Management**:

   - Views can help in managing and presenting data in a more meaningful way. For instance, you can create a view that consolidates data from different sources or formats it for easier consumption.

   7. **Consistency**:

   - By using views, you ensure that the same query logic is applied consistently across different parts of an application or by different users. This reduces errors and discrepancies.

4. **Usage**:

- Selecting Data from a View:

  ```sql
  SELECT * FROM view_name;
  ```

  Retrieves all columns and rows from the view.

  - Filtering Data from a View:

  ```sql
  SELECT column1, column2
  FROM view_name
  WHERE condition;
  ```

Retrieves specific columns and rows based on a condition.

- Updating Data through a View:

  ```sql
  UPDATE view_name
  SET column1 = value
  WHERE condition;
  ```

- Inserting Data through a View:

  ```sql
  INSERT INTO view_name (column1, column2)
  VALUES (value1, value2);
  ```

- Deleting Data through a View:

  ```sql
  DELETE FROM view_name
  WHERE condition;

  ```

- Dropping a View:

  ```sql
  DROP VIEW view_name;
  ```

  Removes the view from the database.

5. **Types of Views**:

- **Simple Views**: Based on a single table.
- **Complex Views**: Based on multiple tables and can include joins, aggregations, and subqueries.

6. **Updatable Views**:

- Some views are updatable, meaning you can perform `INSERT`, `UPDATE`, and `DELETE` operations through them. This depends on how the view is defined.

7.  **Materialized Views(PostgreSQL specific)**:

- Unlike regular views, materialized views store the result set of the query physically. They can be refreshed periodically to keep the data up to date.

8. **Examples**:

- Create a View:

  ```sql
  CREATE VIEW expensive_cars AS
  SELECT id,make, model, model_year, price
  FROM car
  WHERE model_year >= '2000'
  ORDER BY price DESC;
  ```

- Select from View:

  ```sql
  SELECT * FROM expensive_cars;
  ```

- Update through View:

  ```sql
  UPDATE expensive_cars
  SET price = 60000
  WHERE id = 196;
  ```

- Drop View:

  ```sql
  DROP VIEW expensive_cars;
  ```
