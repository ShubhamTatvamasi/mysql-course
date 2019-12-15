# aggregate-functions

count
```sql
SELECT COUNT(*) FROM books;

SELECT COUNT(DISTINCT author_fname) FROM books;

SELECT COUNT(DISTINCT author_lname, author_fname) FROM books;

SELECT COUNT(*) FROM books WHERE title LIKE '%the%';
```

group by
```sql
SELECT author_lname, COUNT(*) FROM books
GROUP BY author_lname;

SELECT author_fname, author_lname, COUNT(*) FROM books
GROUP BY author_lname, author_fname;

SELECT released_year, COUNT(*) FROM books GROUP BY released_year;

SELECT
  CONCAT(
    'IN ', released_year, ' ', COUNT(*), ' book(s) released'
  ) AS 'books released'
FROM books GROUP BY released_year;
```

check modes enabled on mysql
```sql
SHOW VARIABLES LIKE 'sql_mode';
```
delete ONLY_FULL_GROUP_BY from the sql_mode
```sql
SET GLOBAL sql_mode=(SELECT REPLACE(@@sql_mode,'ONLY_FULL_GROUP_BY,',''));
```

min and max
```sql
SELECT MIN(released_year) FROM books;
SELECT MIN(pages) FROM books;

SELECT MAX(released_year) FROM books;
SELECT MAX(pages) FROM books;

SELECT MIN(title) FROM books;
SELECT MAX(title) FROM books;

SELECT * FROM books WHERE pages = (SELECT MIN(pages) FROM books);
SELECT * FROM books WHERE pages = (SELECT MAX(pages) FROM books);

SELECT title, pages FROM books WHERE pages = (SELECT MIN(pages) FROM books);
SELECT title, pages FROM books WHERE pages = (SELECT MAX(pages) FROM books);

SELECT * FROM books ORDER BY pages ASC LIMIT 1;
SELECT * FROM books ORDER BY pages DESC LIMIT 1;

SELECT title, pages FROM books ORDER BY pages ASC LIMIT 1;
SELECT title, pages FROM books ORDER BY pages DESC LIMIT 1;

SELECT author_fname, author_lname, MIN(released_year)
FROM books
GROUP BY author_lname, author_fname;

SELECT author_fname, author_lname, MAX(pages)
FROM books
GROUP BY author_lname, author_fname;
```

sum
```sql
SELECT SUM(pages) FROM books;

SELECT SUM(released_year) FROM books;

SELECT author_fname, author_lname, SUM(pages) FROM books
GROUP BY author_fname, author_lname;
```

avg
```sql
SELECT AVG(released_year) FROM books;

SELECT AVG(pages) FROM books;

SELECT released_year, AVG(stock_quantity) FROM books
GROUP BY released_year;

SELECT author_fname, author_lname, AVG(pages) FROM books
GROUP BY author_lname, author_fname;
```

```sql
SELECT COUNT(*) FROM books;

SELECT released_year, COUNT(*) AS 'book released'
FROM books GROUP BY released_year;

SELECT SUM(stock_quantity) FROM books;

SELECT author_fname, author_lname, AVG(released_year) FROM books
GROUP BY author_fname, author_lname;

SELECT CONCAT(author_fname, ' ', author_lname) AS 'full name of author who wrote longest book'
FROM books
WHERE pages = (SELECT MAX(pages) FROM books);

SELECT released_year AS 'year',
  COUNT(released_year) AS '# books',
  AVG(pages) AS 'avg pages'
FROM books
GROUP BY released_year;
```
