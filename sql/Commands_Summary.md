# SQL Commands Summary

## Login an DB (via CMD)

```bash
 mysql -u username -p -h localhost
```

## Database Create, Delete

| Description                 | SQL                                   |
|-----------------------------|---------------------------------------|
| Create a database           | `CREATE DATABASE test;`               |
| Create only if not existing | `CREATE DATABASE IF NOT EXISTS test;` |
| Select a database           | `USE test;`                           |
| Delete a database           | `DROP DATABASE test;`                 |
| Delete a database if exists | `DROP DATABASE test IF EXISTS;`       |

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

| Description                    | SQL                                                                             |
|--------------------------------|---------------------------------------------------------------------------------|
| Add a new column               | `ALTER TABLE student ADD nachname VARCHAR(100);`                                |
| Add a new column               | `ALTER TABLE student ADD COLUMN (nachname VARCHAR(100), vorname VARCHAR(100));` |
| Add a column after another     | `ALTER TABLE student ADD nachname VARCHAR(100) AFTER vorname;`                  |
| Rename a column/field          | `ALTER TABLE student RENAME COLUMN nachname TO lastname;`                       |
| Rename + change datatype       | `ALTER TABLE employee CHANGE name last_name VARCHAR(100);`                      |
| Delete a column/field          | `ALTER TABLE student DROP lastname;`                                            |
| Delete a column/field          | `ALTER TABLE employee DROP COLUMN nickname;`                                    |
| Modify datatype or constraints | `ALTER TABLE persons MODIFY COLUMN Age INT NOT NULL;`                           |

## Data Types

### String Data Types


| Type                   | Description                 |
|:-----------------------|:----------------------------|
| `CHAR(size)`           | Fixed-length string         |
| `VARCHAR(size)`        | Variable-length string      |
| `BINARY(size)`         | Fixed-length binary         |
| `VARBINARY(size)`      | Variable-length binary      |
| `TINYBLOB`             | Small binary object         |
| `TINYTEXT`             | Small text                  |
| `TEXT`                 | Medium text                 |
| `BLOB`                 | Medium binary               |
| `MEDIUMTEXT`           | Larger text                 |
| `MEDIUMBLOB`           | Larger binary               |
| `LONGTEXT`             | Very large text             |
| `LONGBLOB`             | Very large binary           |
| `ENUM("one","two"...)` | One value from a list       |
| `SET(...)`             | Multiple values from a list |

### Numeric Data Types

| Type               | Description                                                                                                   |
|:-------------------|:--------------------------------------------------------------------------------------------------------------|
| `BIT(size)`        | Stores 1–64 bits. Good for flags but not very readable TINYINT/BOOL is often more practical.                  |
| `TINYINT`          | Very small integer (−128–127). Good for small status values. Display width is irrelevant today.               |
| `BOOL / BOOLEAN`   | Alias for TINYINT(1). **Not a true Boolean** easy misconception.                                              |
| `SMALLINT`         | Small integer (−32k–32k). Saves little space compared to INT.                                                 |
| `MEDIUMINT`        | Medium integer (−8M–8M). Rarely necessary; INT is usually simpler.                                            |
| `INT / INTEGER`    | Standard integer (−2.1B–2.1B). Usually the best default choice.                                               |
| `BIGINT`           | Very large integer (up to 9e18). Useful for big IDs or millisecond timestamps.                                |
| `FLOAT(p)`         | Floating-point (approximate). **Not reliable for exact values** like money.                                   |
| `DOUBLE`           | Larger floating-point number (also approximate).                                                              |
| `DECIMAL(size, d)` | **Exact** numeric type. Perfect for currencies or any values requiring precision. Max 65 digits, 30 decimals. |

### Date and Time Data Types

| Type             | Description                                                                                                              |
|:-----------------|:-------------------------------------------------------------------------------------------------------------------------|
| `DATE`           | Stores only a **calendar date** (YYYY-MM-DD). Range: **1000–9999**.                                                      |
| `DATETIME(fsp)`  | Stores **date + time**. No timezone. Range: **1000–9999**. Supports automatic DEFAULT/ON UPDATE.                         |
| `TIMESTAMP(fsp)` | Stores **seconds since Unix epoch**. Timezone-aware (internally). Range: **1970–2038**. Supports auto DEFAULT/ON UPDATE. |
| `TIME(fsp)`      | Stores only a **time span** (hh:mm:ss), not a date. Range is huge: **–838:59:59 to 838:59:59**.                          |
| `YEAR`           | 4-digit year (1901–2155 + 0000). No more 2-digit format in MySQL 8+.                                                     |

>* fsp is the fractional seconds precision

## INSERT Data

| Description | SQL                                           |
|-------------|-----------------------------------------------|
| Insert data | `INSERT INTO table (fields) VALUES (values);` |

### Examples 

```SQL
INSERT INTO employee
(first_name,last_name,adress,address2,city,zip,phone,dob,salary,employment,civilstatus,childallowance)
VALUES 
("Maria","Solti","Südhangweg 5","","Bern","3006","+41556661234","2001-10-04", 6500, 75,"single",0),
("Mario","Kienthal","Am Fluss 3","Block 3","Zürich","8004","+41994443214","2002-03-04",5400, 60, "single", 0),
("Sascha","Honnegger","Bernstrasse 19","","Oberthal","3609","+41397773311","1998-05-29", 6800, 80, "married", 1);
```

## SELECT

| Description                | SQL                                  |
|----------------------------|--------------------------------------|
| Select all rows            | `SELECT * FROM employee;`            |
| Select specific columns    | `SELECT columnname FROM table;`      |
| Select rows with condition | `SELECT * FROM table WHERE city="";` |

### Examples

```SQL
SELECT name, family_name FROM students 
WHERE name LIKE 'm%'            -- Start's with m [ LIKE / NOT LIKE] **
AND size > 5                    -- Compare with <, >, = etc..
AND age BETWEEN 1 AND 2         -- Between
AND startDate < '2023-01-01'    -- Date
ORDER BY family_name DESC;      -- Order DESC or ASC
-- AND / OR

-- Control foreign keys
SELECT * FROM employee 
    WHERE department NOT IN (SELECT department_id FROM department);

```

> ** See section [WILDCARD](#WILDCARD).

### Nested SELECT

```SQL
SELECT * FROM employee
WHERE department = (
    SELECT department_id FROM department 
    WHERE name = "Developer"
);
```

## WHERE Clause 

> **Note:** The WHERE clause is not only used in `SELECT` statements, it is also used in `UPDATE`, `DELETE`, etc.!

| Operator  | Description                                                                 |
|:----------|:----------------------------------------------------------------------------|
| `=`       | Equal                                                                       |
| `>`       | Greater than                                                                |
| `<`       | Less than                                                                   |
| `>=`      | Greater than or equal                                                       |
| `<=`      | Less than or equal                                                          |
| `<>`      | Not equal. Note: In some versions of SQL this operator may be written as != |
| `BETWEEN` | Between a certain range                                                     |
| `LIKE`    | Search for a pattern                                                        |
| `IN`      | To specify multiple possible values for a column                            |

## Constraints

| SQL              | Description                                              |
|:-----------------|:---------------------------------------------------------|
| `NOT NULL`       | Cannot be NULL                                           |
| `UNIQUE`         | Must be unique                                           |
| `PRIMARY KEY`    | Unique row identifier                                    |
| `CHECK`          | Value restriction                                        |
| `DEFAULT`        | Default value                                            |
| `CREATE INDEX`   | Create an index                                          |
| `AUTO INCREMENT` | Increments value automatically (usefull for table index) |

### Example 

```SQL
CREATE TABLE review (
 review_id INT AUTO_INCREMENT NOT NULL PRIMARY KEY,
 ratingstars TINYINT DEFAULT 3,
 review_date DATETIME DEFAULT CURRENT_TIMESTAMP
 );
```

### Foreign Key

```SQL
ALTER TABLE review 
ADD CONSTRAINT fk_game_review                   -- Relationship name 
FOREIGN KEY (game_id) REFERENCES game(game_id);

ALTER TABLE review DROP FOREIGN KEY fk_user_review; -- Delete Relationship
```

### CHECK 

```SQL
CREATE TABLE tablename (
    age INT CHECK (age >= 18)
);
-------------------------
CREATE TABLE review (
 review_id INT AUTO_INCREMENT NOT NULL PRIMARY KEY,
 ratingstars TINYINT DEFAULT 3 CHECK(ratingstars>0 AND ratingstars<6),
 );
```

## DELETE 

```SQL
DELETE FROM tablename WHERE id = 2;
```

## SET Commands

| Description                | SQL                                       |
|----------------------------|-------------------------------------------|
| Disable foreign-key checks | `SET FOREIGN_KEY_CHECKS = 0;`             |
| Disable safe-update mode   | `SET SQL_SAFE_UPDATES = 0;`               |
| Allows id = 0              | `SET SQL_MODE = "NO_AUTO_VALUE_ON_ZERO";` |

## Import Data

### Show import directory

```SQL
SHOW VARIABLES LIKE 'secure_file_priv';
```

### Load CSV File

```SQL
LOAD DATA INFILE 'path\\to\\file.csv' -- path to the csv file don't forget to use \\ in windows
INTO TABLE destinationtable     -- Destination of the import
FIELDS TERMINATED BY ';'        -- Char that separates the field on the csv file
LINES TERMINATED BY 0x0d0a      -- Hex of end of line
IGNORE 1 LINES                  -- Ignoring the first line on the csv file if necessary
(customer_id, @firstname, @family_name, @dummy, @rankings)  -- **
SET 
    rankings = 20*@ranking;
    name = CONCAT(@firstname, ' ', @family_name);
```

>** The order represents the order of the values on the csv file. The fieldnames can be used to determine what represents what. You can also use the '@' to escape the column or to store that field in a variable. 

## String functions

| Description   | SQL                  |
|---------------|----------------------|
| Concatenation | `CONCAT(val1, val2)` |


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
COMMIT; -- Commit changes 
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

| SQL                             | Description                                                                                 |
|---------------------------------|---------------------------------------------------------------------------------------------|
| `CHECKSUM TABLE note;`          |                                                                                             |
| `CHECKSUM TABLE note EXTENDED;` | This option reads all rows in the table and computes the checksum based on the actual data. |
| `HECKSUM TABLE note QUICK;`     | It only checks for structural changes in the table.                                         |

### Why Use the CHECKSUM TABLE Statement?

- Detect Data Corruption;
- Verify Data Consistency;
- Validate Data Integrity after Backups;

## WILDCARD

| Symbol | Description                        | Example                             |
|--------|------------------------------------|-------------------------------------|
| %      | Represents zero or more characters | bl% finds bl, black, blue, and blob |
| _      | Represents a single character      | h_t finds hot, hat, and hit         |

| LIKE Operator                   | Description                                                                   |
|---------------------------------|-------------------------------------------------------------------------------|
| WHERE CustomerName LIKE 'a%'    | Finds any values that starts with "a"                                         |
| WHERE CustomerName LIKE '%a'    | Finds any values that ends with "a"                                           |
| WHERE CustomerName LIKE '%or%'  | Finds any values that have "or" in any position                               |
| WHERE CustomerName LIKE '_r%'   | Finds any values that have "r" in the second position                         |
| WHERE CustomerName LIKE 'a_%_%' | Finds any values that starts with "a" and are at least 3 characters in length |
| WHERE ContactName LIKE 'a%o'    | Finds any values that starts with "a" and ends with "o"                       |

> Some of the information in these notes was adapted from W3Schools: https://www.w3schools.com/.