# logical-operators

not equal
```sql
SELECT title, released_year FROM books WHERE released_year != 2017;
SELECT title, author_lname FROM books WHERE author_lname != 'Harris';
```

not like
```sql
SELECT title FROM books WHERE title LIKE 'W%';
SELECT title FROM books WHERE title NOT LIKE 'W%';
```

greater than
```sql
SELECT title, released_year FROM books WHERE released_year > 2000 ORDER BY released_year;
```

greater then or equal to
```sql
SELECT title, released_year FROM books WHERE released_year >= 2000 ORDER BY released_year;
SELECT title, stock_quantity FROM books WHERE stock_quantity >= 100 ORDER BY stock_quantity;
```

less than
```sql
SELECT title, released_year FROM books WHERE released_year < 2000 ORDER BY released_year;
```

less than or equal to
```sql
SELECT title, released_year FROM books WHERE released_year <= 2000 ORDER BY released_year;
```

logical and
```sql
SELECT title, author_lname, released_year FROM books WHERE author_lname = 'Eggers' AND released_year > 2010;
SELECT title, author_lname, released_year FROM books WHERE author_lname = 'Eggers' && released_year > 2010;

SELECT title, author_lname, released_year FROM books WHERE author_lname = 'Eggers' AND released_year > 2010 AND title LIKE '%novel%';
```

logical or
```sql
SELECT title, author_lname, released_year FROM books WHERE author_lname = 'Eggers' OR released_year > 2010;
SELECT title, author_lname, released_year FROM books WHERE author_lname = 'Eggers' || released_year > 2010;

SELECT title, author_lname, released_year, stock_quantity FROM books WHERE author_lname = 'Eggers' OR released_year > 2010 OR stock_quantity > 100;
```

between and not between
```sql
SELECT title, released_year FROM books WHERE released_year >= 2004 AND released_year <= 2015;
SELECT title, released_year FROM books WHERE released_year BETWEEN 2004 AND 2015;

SELECT title, released_year FROM books WHERE released_year NOT BETWEEN 2004 AND 2015 ORDER BY released_year;
```

cast
```sql
SELECT CAST('2017-05-02' AS DATETIME);

SELECT name, birthdt FROM people WHERE birthdt BETWEEN '1980-01-01' AND '2000-01-01';

SELECT name, birthdt FROM people WHERE birthdt BETWEEN 
  CAST('1980-01-01' AS DATETIME) AND 
  CAST('2000-01-01' AS DATETIME);
```

in
```sql
SELECT title, author_lname FROM books
WHERE author_lname = 'Carver' OR
      author_lname = 'Lahiri' OR
      author_lname = 'Smith';

SELECT title, author_lname FROM books
WHERE author_lname IN ('Carver', 'Lahiri', 'Smith');

SELECT title, released_year FROM books
WHERE released_year IN (1985, 2017);
```

not in
```sql
SELECT title, released_year FROM books
WHERE released_year NOT IN (2000, 2002, 2004, 2006, 2008, 2010, 2012, 2014, 2016);

SELECT title, released_year FROM books
WHERE released_year >= 2000
AND released_year NOT IN (2000, 2002, 2004, 2006, 2008, 2010, 2012, 2014, 2016);
```

remainder operator
```sql
SELECT title, released_year FROM books
WHERE released_year >= 2000
AND released_year % 2 != 0;
```

case statements
```sql
SELECT title, released_year,
  CASE
    WHEN released_year >= 2000 THEN 'Modern Lit'
    ELSE '20th Century Lit'
  END AS 'GENRE'
FROM books ORDER BY released_year;

SELECT title, stock_quantity,
  CASE
    WHEN stock_quantity BETWEEN 0 AND 50 THEN '*'
    WHEN stock_quantity BETWEEN 51 AND 100 THEN '**'
    ELSE '***'
  END AS 'STOCK'
FROM books;

SELECT title, stock_quantity,
  CASE
    WHEN stock_quantity <= 50 THEN '*'
    WHEN stock_quantity <= 100 THEN '**'
    ELSE '***'
  END AS 'STOCK'
FROM books;
```

exercise
```sql
SELECT title, released_year FROM books WHERE released_year < 1980;

SELECT title, author_lname FROM books
WHERE author_lname IN ('Eggers', 'Chabon');

SELECT title, author_lname, released_year FROM books
WHERE author_lname = 'Lahiri' AND released_year > 2000;

SELECT title, pages FROM books
WHERE pages BETWEEN 100 AND 200;

SELECT title, author_lname FROM books
WHERE author_lname LIKE 'C%' OR author_lname LIKE 'S%';

SELECT title, author_lname FROM books
WHERE SUBSTR(author_lname, 1, 1) IN ('C', 'S');

SELECT title, author_lname,
  CASE
    WHEN title LIKE '%stories%' THEN 'Short Stories'
    WHEN title = 'Just Kids' OR title = 'A Heartbreaking Work of Staggering Genius' THEN 'Memoir'
    ELSE 'Novel'
  END AS 'TYPE'
FROM books;

SELECT author_fname, author_lname,
  CASE
    WHEN COUNT(*) = 1 THEN CONCAT(COUNT(*), ' book')
    ELSE CONCAT(COUNT(*), ' books')
  END AS 'COUNT'
FROM books GROUP BY author_lname, author_fname;
```
