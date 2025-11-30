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
