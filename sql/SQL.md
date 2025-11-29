# SQL 

## Login an DB (via CMD)

```SQL
 mysql -u xyz -p -h localhost
```

## Datenbank erstellen, auswählen und löschen
```SQL
CREATE DATABASE IF NOT EXISTS test;
USE test;
DROP DATABASE test;
```

## Tabelle erstellen, umbenennen und löschen

```SQL
CREATE TABLE student(id INT, name VARCHAR 100));
RENAME TABLE student TO student_old;
DROP TABLE student;
DROP TABLE IF EXISTS employee;
```

## Datenfelder hinzufügen, umbenennen und löschen

```SQL
ALTER TABLE student ADD nachname VARCHAR(100);
ALTER TABLE student RENAME COLUMN nachname TO lastname;
ALTER TABLE employee CHANGE name last_name VARCHAR(100);
ALTER TABLE student DROP lastname;
ALTER TABLE employee DROP COLUMN nickname;
```

## Tabelle beschreiben

Displays Datatype

```SQL
DESC student;
```

## Tabelle kopieren

```SQL
CREATE TABLE teacher LIKE student;
```

## Data types

| Data type                   | Description                                                                                                                                                                                                                                                             |
| --------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| CHAR(size)                  | A FIXED length string (can contain letters, numbers, and special characters). The _size_ parameter specifies the column length in characters - can be from 0 to 255. Default is 1                                                                                       |
| VARCHAR(size)               | A VARIABLE length string (can contain letters, numbers, and special characters). The _size_ parameter specifies the maximum string length in characters - can be from 0 to 65535                                                                                        |
| BINARY(size)                | Equal to CHAR(), but stores binary byte strings. The _size_ parameter specifies the column length in bytes. Default is 1                                                                                                                                                |
| VARBINARY(size)             | Equal to VARCHAR(), but stores binary byte strings. The _size_ parameter specifies the maximum column length in bytes.                                                                                                                                                  |
| TINYBLOB                    | For BLOBs (Binary Large Objects). Max length: 255 bytes                                                                                                                                                                                                                 |
| TINYTEXT                    | Holds a string with a maximum length of 255 characters                                                                                                                                                                                                                  |
| TEXT(size)                  | Holds a string with a maximum length of 65,535 bytes                                                                                                                                                                                                                    |
| BLOB(size)                  | For BLOBs (Binary Large Objects). Holds up to 65,535 bytes of data                                                                                                                                                                                                      |
| MEDIUMTEXT                  | Holds a string with a maximum length of 16,777,215 characters                                                                                                                                                                                                           |
| MEDIUMBLOB                  | For BLOBs (Binary Large Objects). Holds up to 16,777,215 bytes of data                                                                                                                                                                                                  |
| LONGTEXT                    | Holds a string with a maximum length of 4,294,967,295 characters                                                                                                                                                                                                        |
| LONGBLOB                    | For BLOBs (Binary Large Objects). Holds up to 4,294,967,295 bytes of data                                                                                                                                                                                               |
| ENUM(val1, val2, val3, ...) | A string object that can have only one value, chosen from a list of possible values. You can list up to 65535 values in an ENUM list. If a value is inserted that is not in the list, a blank value will be inserted. The values are sorted in the order you enter them |
| SET(val1, val2, val3, ...)  | A string object that can have 0 or more values, chosen from a list of possible values. You can list up to 64 values in a SET list                                                                                                                                       |