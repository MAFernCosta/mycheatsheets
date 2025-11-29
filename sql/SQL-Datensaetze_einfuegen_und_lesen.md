# SQL - Datensätze einfügen und lesen

## Datensätze einfügen 

```SQL
INSERT INTO employee
(first_name,last_name,adress,address2,city,zip,phone,dob,salary,employment,civilstatus,childallowance)
VALUES 
("Maria","Solti","Südhangweg 5","","Bern","3006","+41556661234","2001-10-04", 6500, 75,"single",0),
("Mario","Kienthal","Am Fluss 3","Block 3","Zürich","8004","+41994443214","2002-03-04",5400, 60, "single", 0),
("Sascha","Honnegger","Bernstrasse 19","","Oberthal","3609","+41397773311","1998-05-29", 6800, 80, "married", 1);
```

## Datensätze auflisten 

```SQL
SELECT * FROM employee;

SELECT first_name, last_name, salary FROM employee;
```

## "Muss" Spalten definieren 

```SQL

 ALTER TABLE employee MODIFY last_name VARCHAR(100) NOT NULL;
 
```

## Datensätze löschen 
```SQL
DELETE FROM employee WHERE city="Bern";
```
