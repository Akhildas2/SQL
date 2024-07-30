# Data Types

SQL supports a wide range of data types, which can be categorized into several groups. Below are some of the most commonly used data types along with examples of how they are used.

## Numeric Types

### 1. `INTEGER`

A simple integer value.

```sql
CREATE TABLE example_table (
    id INTEGER
);
```

### 2. `SERIAL`

An auto-incrementing integer.

```sql
CREATE TABLE example_table (
    id SERIAL PRIMARY KEY
);
```

### 3. `BIGINT`

A large integer value.

```sql
CREATE TABLE example_table (
    large_value BIGINT
);
```

### 4. `NUMERIC`

A variable-precision number.

```sql
CREATE TABLE example_table (
    precise_value NUMERIC(10, 2)
);
```

### 5. `REAL`

A single-precision floating-point number.

```sql
CREATE TABLE example_table (
    real_value REAL
);

```

## Character Types

### 1. `VARCHAR`

A variable-length string.

```sql
CREATE TABLE example_table (
    name VARCHAR(50)
);
```

### 2. `CHAR`

A fixed-length string.

```sql
CREATE TABLE example_table (
    code CHAR(10)
);
```

### 3. `TEXT`

A variable-length string with no specific length limit.

```sql
CREATE TABLE example_table (
    description TEXT
);
```

## Date/Time Types

### 1. `DATE`

A date value.

```sql
CREATE TABLE example_table (
    birthdate DATE
);
```

### 2. `TIME`

A time of day value.

```sql
CREATE TABLE example_table (
    appointment TIME
);
```

### 3. `TIMESTAMP`

A date and time value.

```sql
CREATE TABLE example_table (
    event TIMESTAMP
);
```

```sql
SELECT NOW(); -- returns a current date, time
SELECT NOW()::DATE; -- returns current date
SELECT NOW()::TIME; -- returns current time
SELECT NOW() - INTERVAL '1 YEAR'; -- substracts one Year
SELECT NOW() + INTERVAL '1 MONTHS'; -- Adds one Month
SELECT EXTRACT(YEAR FROM NOW());-- Extracting the year from the current timestamp
SELECT EXTRACT(DAY FROM NOW());-- Extracting the day of the month from the current timestamp
```

### 4. `INTERVAL`

A time interval.

```sql
CREATE TABLE example_table (
    duration INTERVAL
);
```

## Boolean Type

### 1. `BOOLEAN`

A true or false value.

```sql
CREATE TABLE example_table (
    is_active BOOLEAN
);
```

## Enumerated Types

### 1. `ENUM`

A static, ordered set of values.

```sql
CREATE TYPE mood AS ENUM ('sad', 'ok', 'happy');

CREATE TABLE example_table (
    current_mood mood
);
```

## Array Types

### 1. `ARRAY`

A collection of values.

```sql
CREATE TABLE example_table (
    numbers INTEGER[]
);
```

## JSON Types

### 1. `JSON`

A JSON data type.

```sql
CREATE TABLE example_table (
    data JSON
);
```

### 2. `JSONB`

A binary JSON data type (more efficient).

```sql
CREATE TABLE example_table (
    data JSONB
);
```

## UUID Type

### 1. `UUID`

A universally unique identifier.

```sql
CREATE TABLE example_table (
    unique_id UUID
);
```

## Range Types

### 1. `INT4RANGE`

A range of integer values.

```sql
CREATE TABLE example_table (
    int_range INT4RANGE
);
```

### 2. `TSRANGE`

A range of timestamp values.

```sql
CREATE TABLE example_table (
    ts_range TSRANGE
);
```
