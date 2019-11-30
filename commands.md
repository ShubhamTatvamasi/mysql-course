# commands

show databases
```sql
SHOW DATABASES;
```

create new database
```sql
CREATE DATABASE hello_world_db;
```

use database
```sql
USE hello_world_db;
```

show current database
```sql
SELECT database();
```

delete database
```sql
DROP DATABASE hello_world_db;
```
---

create table in cat_app database
```sql
CREATE DATABASE cat_app;
```
```sql
CREATE TABLE cats
  (
    name VARCHAR(100),
    age INT
  );
```

show tables
```sql
SHOW TABLES;
```

show columns from table
```sql
SHOW COLUMNS FROM cats;
DESC cats;
```

delete tables
```sql
DROP TABLE cats;
```
---

table challenge
```sql
CREATE TABLE pastries
  (
    name VARCHAR(50),
    quantity INT
  );
```
```sql
DESC pastries;
```
```sql
DROP TABLE pastries;
```
---

insert data into tables
```sql
INSERT INTO cats(name, age)
VALUES ('Jetson', 7);
```
```sql
INSERT INTO cats(age, name) VALUES (11, 'Draco');
```

multiple insert
```sql
INSERT INTO cats(name, age)
VALUES ('Charlie', 10),
       ('Sadie', 3),
       ('Lazy Bear', 1);
```

view all data from a table
```sql
SELECT * FROM cats;
```
---

insert challenge
```sql
CREATE TABLE people
  (
    first_name VARCHAR(20),
    last_name VARCHAR(20),
    age INT
  );
```
```sql
INSERT INTO people(first_name, last_name, age)
VALUES ('Tina', 'Belcher', 13);
```
```sql
INSERT INTO people(age, first_name, last_name)
VALUES (42, 'Bob', 'Belcher');
```
```sql
INSERT INTO people(first_name, last_name, age)
VALUES ('Linda', 'Belcher', 45),
       ('Phillip', 'Frond', 38),
       ('Calvin', 'Fischoeder', 70);
```
```sql
SELECT * FROM people;
```
---
