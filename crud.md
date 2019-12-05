# crud

Recreate a new cats table:
```sql
CREATE TABLE cats
  (
     cat_id INT NOT NULL AUTO_INCREMENT PRIMARY KEY,
     name VARCHAR(100),
     breed VARCHAR(100),
     age INT
  );
```

And finally insert some new cats:
```sql
INSERT INTO cats(name, breed, age) 
VALUES ('Ringo', 'Tabby', 4),
       ('Cindy', 'Maine Coon', 10),
       ('Dumbledore', 'Maine Coon', 11),
       ('Egg', 'Persian', 4),
       ('Misty', 'Tabby', 13),
       ('George Michael', 'Ragdoll', 9),
       ('Jackson', 'Sphynx', 7);
```

Various Simple SELECT statements:
```sql
SELECT * FROM cats; 

SELECT name FROM cats; 

SELECT age FROM cats; 

SELECT cat_id FROM cats; 

SELECT name, age FROM cats; 

SELECT cat_id, name, age FROM cats; 

SELECT age, breed, name, cat_id FROM cats; 

SELECT cat_id, name, age, breed FROM cats; 
```
---

CODE: Introduction to WHERE

Select by age:
```sql
SELECT * FROM cats WHERE age=4; 
```
Select by name:
```sql
SELECT * FROM cats WHERE name='Egg'; 
```
Notice how it deals with case:
```sql
SELECT * FROM cats WHERE name='egG'; 
```
challenge
```sql
SELECT cat_id FROM cats; 
SELECT name, breed FROM cats; 
SELECT name, age FROM cats WHERE breed='Tabby'; 
SELECT cat_id, age FROM cats WHERE cat_id=age; 
SELECT * FROM cats WHERE cat_id=age;
```
---

CODE: Introduction to Aliases
```sql
SELECT cat_id AS id, name FROM cats;

SELECT name AS 'cat name', breed AS 'kitty breed' FROM cats;

DESC cats;
```
---

CODE: Updating Data

Change tabby cats to shorthair:
```sql
UPDATE cats SET breed='Shorthair' WHERE breed='Tabby'; 
```
Another update:
```sql
UPDATE cats SET age=14 WHERE name='Misty'; 
```
try select before everything you update things 
```sql
SELECT * FROM cats WHERE name='Misty'; 
```
---

CODE: Update Challenges Solution
```sql
SELECT * FROM cats WHERE name='Jackson';

UPDATE cats SET name='Jack' WHERE name='Jackson';

SELECT * FROM cats WHERE name='Jackson';

SELECT * FROM cats WHERE name='Jack';

SELECT * FROM cats WHERE name='Ringo';

UPDATE cats SET breed='British Shorthair' WHERE name='Ringo';

SELECT * FROM cats WHERE name='Ringo';

SELECT * FROM cats;

SELECT * FROM cats WHERE breed='Maine Coon';

UPDATE cats SET age=12 WHERE breed='Maine Coon';

SELECT * FROM cats WHERE breed='Maine Coon';
```
---

CODE: DELETING DATA
```sql
DELETE FROM cats WHERE name='Egg';

SELECT * FROM cats;

SELECT * FROM cats WHERE name='egg';

DELETE FROM cats WHERE name='egg';

SELECT * FROM cats;

DELETE FROM cats;
```

CODE: DELETE Challenges Solution
```sql
SELECT * FROM cats WHERE age=4;

DELETE FROM cats WHERE age=4;

SELECT * FROM cats WHERE age=4;

SELECT * FROM cats;

SELECT *  FROM cats WHERE cat_id=age;

DELETE FROM cats WHERE cat_id=age;

DELETE FROM cats;

SELECT * FROM cats;
```
