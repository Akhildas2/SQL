# Basic Commands

## Basic PostgreSQL Commands for Connecting to `psql` on Windows

### Connecting to `psql`

- **Connect to `psql`:**

```sql
 psql -U postgres
```

Replace postgres with your PostgreSQL username.

- **Enter Password:**
  You will be prompted to enter your password after running the above command. Simply type your password (e.g., postgres) and press Enter.

- **Connect to a Database:**

  ```sql
  \c database_name
  ```

  Replace database_name with the name of your database.

### Useful Commands

- **List all databases:**

```sql
 \l
```

- **List all tables in the current database:**

  ```sql
  \d
  ```

- **Execute SQL commands from a file:**

```sql
 \i /path/to/sql/file.sql
```

Replace /path/to/sql/file.sql with the actual path to your SQL file.

## Database Basic Commands

### Creating a Database

```sql
CREATE DATABASE database_name;
```

Replace database_name with the name of the database you want to create.

### Deleting a Database

```sql
DROP DATABASE database_name;
```

Replace database_name with the name of the database you want to delete.

### Backup a Database
To back up a database, use the pg_dump utility from the command line:

sh

```sql
pg_dump -U username database_name > backup_file.sql
```

Replace username with your PostgreSQL username, database_name with the name of the database you want to back up, and backup_file.sql with the name of the backup file.

### Rename a Database

```sql
ALTER DATABASE old_database_name RENAME TO new_database_name;

```

Replace old_database_name with the current name of the database and new_database_name with the new name you want to give to the database.