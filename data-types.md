# data-types

varchar
```sql
CREATE DATABASE new_testing_db;
use new_testing_db;

CREATE TABLE dogs (name CHAR(5), breed VARCHAR(10));

INSERT INTO dogs (name, breed) VALUES ('bob', 'beagle');
INSERT INTO dogs (name, breed) VALUES ('robby', 'corgi');
INSERT INTO dogs (name, breed) VALUES ('Princess Jane', 'Retriever');
INSERT INTO dogs (name, breed) VALUES ('Princess Jane', 'Retrieverlongverylong');
```
> CHAR has a fixed length

check modes enabled on mysql
```sql
SHOW VARIABLES LIKE 'sql_mode';
```
delete ONLY_FULL_GROUP_BY FROM the sql_mode
```sql
SET GLOBAL sql_mode=(SELECT REPLACE(@@sql_mode,'STRICT_TRANS_TABLES,',''));
```

int
```sql
CREATE TABLE items (price DECIMAL(5,2));

INSERT INTO items(price) VALUES(7);
INSERT INTO items(price) VALUES(79238472);
INSERT INTO items(price) VALUES(34.88);
INSERT INTO items(price) VALUES(298.9999);
INSERT INTO items(price) VALUES(1.9999);
```

float
```sql
CREATE TABLE thingies (price FLOAT);

INSERT INTO thingies(price) VALUES (88.45);
INSERT INTO thingies(price) VALUES (8877.45);
INSERT INTO thingies(price) VALUES (8877665544.45);
```

date, time, datetime
```sql
CREATE TABLE people (
  name VARCHAR(100),
  birthdate DATE,
  birthtime TIME,
  birthdt DATETIME
);

INSERT INTO people (name, birthdate, birthtime, birthdt) VALUES
('Padma', '1983-11-11', '10:07:35', '1983-11-11 10:07:35'),
('Larry', '1943-12-25', '04:10:42', '1943-12-25 04:10:42');


SELECT name, birthdate FROM people;
SELECT name, birthdate, DAY(birthdate) FROM people;
SELECT name, birthdate, DAYNAME(birthdate) FROM people;
SELECT name, birthdate, DAYOFWEEK(birthdate) FROM people;
SELECT name, birthdate, DAYOFYEAR(birthdate) FROM people;

SELECT name, birthdt, DAYOFYEAR(birthdt) FROM people;
SELECT name, birthdt, MONTH(birthdt) FROM people;
SELECT name, birthdt, MONTHNAME(birthdt) FROM people;

SELECT name, birthtime, HOUR(birthtime) FROM people;
SELECT name, birthtime, MINUTE(birthtime) FROM people;

SELECT name, birthdate, DATE_FORMAT(birthdate, '%D %M %Y') FROM people;

SELECT DATE_FORMAT(birthdt, 'was born on %W') FROM people;
SELECT DATE_FORMAT(birthdt, '%m/%d/%Y') FROM people;
SELECT DATE_FORMAT(birthdt, '%m/%d/%Y at %h:%m') FROM people;

SELECT name, birthdate, DATEDIFF(NOW(), birthdate) FROM people;

SELECT birthdt, DATE_ADD(birthdt, INTERVAL 1 MONTH) FROM people;
SELECT birthdt, DATE_ADD(birthdt, INTERVAL 10 SECOND) FROM people;
SELECT birthdt, DATE_ADD(birthdt, INTERVAL 3 QUARTER) FROM people;

SELECT birthdt, birthdt + INTERVAL 1 MONTH FROM people;
SELECT birthdt, birthdt - INTERVAL 5 MONTH FROM people;

SELECT birthdt, birthdt + INTERVAL 15 MONTH + INTERVAL 10 HOUR FROM people;
```

timestamp
```sql
CREATE TABLE comments (
  content VARCHAR(100),
  created_at TIMESTAMP DEFAULT NOW()
);

INSERT INTO comments (content) VALUES('lol what a funny article');
INSERT INTO comments (content) VALUES('I found this offensive');
INSERT INTO comments (content) VALUES('sakjadakjdhajkdh');

SELECT * FROM comments ORDER BY created_at;
SELECT * FROM comments ORDER BY created_at DESC;
```
```sql
CREATE TABLE comments2 (
  content VARCHAR(100),
  changed_at TIMESTAMP DEFAULT NOW() ON UPDATE CURRENT_TIMESTAMP
);

INSERT INTO comments2 (content) VALUES('lol what a funny article');
INSERT INTO comments2 (content) VALUES('I found this offensive');
INSERT INTO comments2 (content) VALUES('sakjadakjdhajkdh');
INSERT INTO comments2 (content) VALUES('I LIKE CATS AND DOGS');

UPDATE comments2 SET content='THIS IS NOT GIBBERISH' WHERE content='sakjadakjdhajkdh';

SELECT * FROM comments2 ORDER BY changed_at;
```

What's a good use case for CHAR?
------
Used for text that we know has a fixed length, e.g., State abbreviations, abbreviated company names, sex M/F, etc.
```sql
CREATE TABLE inventory (
    item_name VARCHAR(100),
    price DECIMAL(8,2),
    quantity INT
);
```
What's the difference between DATETIME and TIMESTAMP?
------
They both store datetime information, but there's a difference in the range, TIMESTAMP has a smaller range. TIMESTAMP also takes up less space. 

TIMESTAMP is used for things like meta-data about when something is created or updated.
```sql
SELECT CURTIME();

SELECT CURDATE();

SELECT DAYOFWEEK(CURDATE());
SELECT DAYOFWEEK(NOW());
SELECT DATE_FORMAT(NOW(), '%w') + 1;

SELECT DAYNAME(NOW());
SELECT DATE_FORMAT(NOW(), '%W');

SELECT DATE_FORMAT(CURDATE(), '%m/%d/%Y');

SELECT DATE_FORMAT(NOW(), '%M %D at %h:%i');

CREATE TABLE tweets(
    content VARCHAR(140),
    username VARCHAR(20),
    created_at TIMESTAMP DEFAULT NOW()
);

INSERT INTO tweets (content, username) VALUES('this is my first tweet', 'coltscat');
SELECT * FROM tweets;

INSERT INTO tweets (content, username) VALUES('this is my second tweet', 'coltscat');
SELECT * FROM tweets;
```
