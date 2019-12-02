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
```sql
DROP TABLE people;
```
---

show warnings
```sql
SHOW WARNINGS;
```
---

Try inserting a cat without an age:
```sql
INSERT INTO cats(name) VALUES('Alabama');
```

Try inserting a nameless and ageless cat:
```sql
INSERT INTO cats() VALUES();
```

Define a new cats2 table with NOT NULL constraints:
```sql
CREATE TABLE cats2
  (
    name VARCHAR(100) NOT NULL,
    age INT NOT NULL
  );
```

Now try inserting an ageless cat:
```sql
INSERT INTO cats2(name) VALUES('Texas');
```
---

Define a table with a DEFAULT name specified:
```sql
CREATE TABLE cats3
  (
    name VARCHAR(20) DEFAULT 'unnamed',
    age INT DEFAULT 99
  );
```

Insert a cat without a name:
```sql
INSERT INTO cats3(age) VALUES(13);
```
---

Combine NOT NULL and DEFAULT:
```sql
CREATE TABLE cats4
  (
    name VARCHAR(20) NOT NULL DEFAULT 'unnamed',
    age INT NOT NULL DEFAULT 99
  );
```
---

Define a table with a PRIMARY KEY constraint:
```sql
CREATE TABLE unique_cats
  (
    cat_id INT NOT NULL,
    name VARCHAR(100),
    age INT,
    PRIMARY KEY (cat_id)
  );
```

Insert some new cats:
```sql
INSERT INTO unique_cats(cat_id, name, age) VALUES(1, 'Fred', 23);
INSERT INTO unique_cats(cat_id, name, age) VALUES(2, 'Louise', 3);
```
---

Adding in AUTO_INCREMENT:
```sql
CREATE TABLE unique_cats2 (
    cat_id INT NOT NULL AUTO_INCREMENT,
    name VARCHAR(100),
    age INT,
    PRIMARY KEY (cat_id)
);
```

INSERT a couple new cats:
```sql
INSERT INTO unique_cats2(name, age) VALUES('Skippy', 4);
INSERT INTO unique_cats2(name, age) VALUES('Jiff', 3);
INSERT INTO unique_cats2(name, age) VALUES('Jiff', 3);
INSERT INTO unique_cats2(name, age) VALUES('Jiff', 3);
INSERT INTO unique_cats2(name, age) VALUES('Skippy', 4);
```
---

Defining The employees table:
```sql
CREATE TABLE employees (
    id INT AUTO_INCREMENT NOT NULL PRIMARY KEY,
    first_name VARCHAR(255) NOT NULL,
    last_name VARCHAR(255) NOT NULL,
    middle_name VARCHAR(255),
    age INT NOT NULL,
    current_status VARCHAR(255) NOT NULL DEFAULT 'employed'
);
```

A test INSERT:
```sql
INSERT INTO employees(first_name, last_name, age) VALUES
('Dora', 'Smith', 58);
```
---


---
Future commands
```sql
ALTER TABLE cats ADD email varchar(255);
ALTER TABLE cats MODIFY COLUMN email varchar(100);
UPDATE INSERT INTO cats(age, name, email) VALUES (11, 'Draco', 'io@123.com');

UPDATE cats 
SET 
    email = 'mary@a.com'
WHERE
    name = 'Jetson';
```
