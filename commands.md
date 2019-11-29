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
