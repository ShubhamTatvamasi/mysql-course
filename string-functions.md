# string-functions

run sql query from a file inside mysql
```sql
source first_file.sql
source testing/insert.sql
```

execute sql file from docker
```bash
docker exec -i mysql mysql -u root -ppassword cat_app < first_file.sql
docker exec -i mysql mysql -u root -ppassword cat_app < testing/insert.sql
```
> cat_app is the database 
---

```sql
CREATE DATABASE book_shop;
```

create table and insert values
```bash
docker exec -i mysql mysql -u root -ppassword book_shop < book_data.sql
```
---

concat
```sql
SELECT CONCAT(author_fname, ' ', author_lname) FROM books;
SELECT CONCAT(author_fname, ' ', author_lname) AS 'Full Name' FROM books;

SELECT author_fname AS 'first', author_lname AS 'last',
CONCAT(author_fname, ' ', author_lname) AS 'full' FROM books;

SELECT CONCAT(title, '-', author_fname, '-', author_lname) FROM books;
```

concat_ws
```sql
SELECT CONCAT_WS(' - ', title, author_fname, author_lname) FROM books;
```
---

substring
```sql
SELECT SUBSTRING('Hello World', 1, 4);
SELECT SUBSTRING('Hello World', 7);
SELECT SUBSTRING('Hello World', -3);

SELECT SUBSTRING(title, 1, 10) AS 'short title' FROM books;
```
```sql
SELECT CONCAT
    (
        SUBSTRING(title, 1, 10),
        '...'
    ) AS 'short title'
FROM books;
```

substr
```sql
SELECT SUBSTR('Hello World', 7);
```
---

