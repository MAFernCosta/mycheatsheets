# SQL Commands Summary

## Login an DB (via CMD)

```bash
 mysql -u xyz -p -h localhost
```

## Database Create, Delete

| Description                 | SQL                                   |
|-----------------------------|---------------------------------------|
| Create a database           | `CREATE DATABASE test;`               |
| Create only if not existing | `CREATE DATABASE IF NOT EXISTS test;` |
| Select a database           | `USE test;`                           |
| Delete a database           | `DROP DATABASE test;`                 |

## Table Create, Rename, Delete

| Description                  | SQL                                                |
|------------------------------|----------------------------------------------------|
| Create a table               | `CREATE TABLE student(id INT, name VARCHAR(100));` |
| Rename a table               | `RENAME TABLE student TO student_old;`             |
| Delete a table               | `DROP TABLE student;`                              |
| Delete table if it exists    | `DROP TABLE IF EXISTS employee;`                   |
| Show table structure         | `DESC table;`                                      |
| Copy a table structure       | `CREATE TABLE teacher LIKE student;`               |
| Delete all rows in a table * | `DELETE FROM tablename;`                           |
 
> ***Note:** `SET SQL_SAFE_UPDATES = 0;`  && `SET SQL_SAFE_UPDATES = 1;`


## Fields Add, Rename, Delete

| Description                    | SQL                                                            |
|--------------------------------|----------------------------------------------------------------|
| Add a new column               | `ALTER TABLE student ADD nachname VARCHAR(100);`               |
| Add a column after another     | `ALTER TABLE student ADD nachname VARCHAR(100) AFTER vorname;` |
| Rename a column                | `ALTER TABLE student RENAME COLUMN nachname TO lastname;`      |
| Rename + change datatype       | `ALTER TABLE employee CHANGE name last_name VARCHAR(100);`     |
| Delete a column                | `ALTER TABLE student DROP lastname;`                           |
| Delete a column                | `ALTER TABLE employee DROP COLUMN nickname;`                   |
| Modify datatype or constraints | `ALTER TABLE Persons MODIFY COLUMN Age INT NOT NULL;`          |

## Data Types

| Description                 | Type              |
|-----------------------------|-------------------|
| Fixed-length string         | `CHAR(size)`      |
| Variable-length string      | `VARCHAR(size)`   |
| Fixed-length binary         | `BINARY(size)`    |
| Variable-length binary      | `VARBINARY(size)` |
| Small binary object         | `TINYBLOB`        |
| Small text                  | `TINYTEXT`        |
| Medium text                 | `TEXT`            |
| Medium binary               | `BLOB`            |
| Larger text                 | `MEDIUMTEXT`      |
| Larger binary               | `MEDIUMBLOB`      |
| Very large text             | `LONGTEXT`        |
| Very large binary           | `LONGBLOB`        |
| One value from a list       | `ENUM(...)`       |
| Multiple values from a list | `SET(...)`        |

## INSERT Data

| Description | SQL                                           |
|-------------|-----------------------------------------------|
| Insert data | `INSERT INTO table (fields) VALUES (values);` |

## SELECT

| Description                | SQL                                  |
|----------------------------|--------------------------------------|
| Select all rows            | `SELECT * FROM employee;`            |
| Select specific columns    | `SELECT columnname FROM table;`      |
| Select rows with condition | `SELECT * FROM table WHERE city="";` |

### More examples

```SQL
SELECT name, family_name FROM students 
WHERE name LIKE 'm%'            -- Start's with m [ LIKE / NOT LIKE]
AND size > 5                    -- Compare with <, >, = etc..
AND age BETWEEN 1 AND 2         -- Between
AND startDate < '2023-01-01'    -- Date
ORDER BY family_name DESC;      -- Order DESC or ASC
-- AND / OR

-- Control foreign keys
SELECT * FROM employee 
    WHERE department NOT IN (SELECT department_id FROM department);

```

### Nested SELECT

```SQL
SELECT * FROM employee
WHERE department = (
    SELECT department_id FROM department 
    WHERE name = "Developer"
);
```

## Constraints

| Description           | SQL            |
|-----------------------|----------------|
| Cannot be NULL        | `NOT NULL`     |
| Must be unique        | `UNIQUE`       |
| Unique row identifier | `PRIMARY KEY`  |
| Value restriction     | `CHECK`        |
| Default value         | `DEFAULT`      |
| Create an index       | `CREATE INDEX` |

### Foreign Key

```sql
ALTER TABLE review 
ADD CONSTRAINT fk_game_review                   -- Relationship name 
FOREIGN KEY (game_id) REFERENCES game(game_id);

ALTER TABLE review DROP FOREIGN KEY fk_user_review; -- Delete Relationship
```

### CHECK 

```sql
CREATE TABLE tablename (
    age INT CHECK (age >= 18)
);
```

## DELETE 

```SQL
DELETE FROM WHERE id = 2;
```

## SET Commands

| Description                | SQL                           |
|----------------------------|-------------------------------|
| Disable foreign-key checks | `SET FOREIGN_KEY_CHECKS = 0;` |
| Disable safe-update mode   | `SET SQL_SAFE_UPDATES = 0;`   |

## Import Data

### Show import directory

```sql
SHOW VARIABLES LIKE 'secure_file_priv';
```

### Load CSV File

```sql
LOAD DATA INFILE 'path/to/file.csv'
INTO TABLE destinationtable
FIELDS TERMINATED BY ';'
LINES TERMINATED BY 0x0d0a
IGNORE 1 LINES
(customer_id, @firstname, @family_name, @dummy, @rankings)
SET 
    rankings = 20*@ranking;
    name = CONCAT(@firstname, ' ', @family_name);
```

## String functions

| Description   | SQL    |
|---------------|--------|
| Concatenation | CONCAT |


## UPDATE 

```SQL
-- Updates the note for all student with id 1
UPDATE note -- Tabel name 
SET note = 6  -- Cellname
WHERE student_id = 1; 
```

## Transaction 

```SQL
SET SESSION autocommit = 0; -- autocommit disable
-- Commands 
Commit; -- Commit changes 
ROLLBACK; -- Rollback the changes
```

### **or**

```SQL
BEGIN; -- Start transaction
-- Commands 
COMMIT; -- STOP the transaction and saves the transaction

ROLLBACK; -- Don't save the trasaction and rollsback
```

## Checksum 

```SQL
CHECKSUM TABLE note;

CHECKSUM TABLE note EXTENDED;

CHECKSUM TABLE note QUICK;
```