# mysql-course

Start mysql server
```bash
docker run -d --name mysql -e MYSQL_ROOT_PASSWORD=password mysql:5.7
```

Get inside mysql 
```bash
docker exec -it mysql mysql --user=root --password=password
```

execute sql file
```bash
docker exec -i mysql mysql --user=root --password=password DATABASE < first_file.sql
```

Stop mysql server
```bash
docker-compose down
```
---

### Backup
```bash
docker exec CONTAINER /usr/bin/mysqldump --user=root --password=password DATABASE > backup.sql
```

### Restore
```bash
cat backup.sql | docker exec -i CONTAINER /usr/bin/mysql --user=root --password=password DATABASE
```
---

Test sql online

https://www.w3schools.com/sql/trysql.asp?filename=trysql_op_or

```sql
SELECT * FROM customers;
SELECT * FROM orders;
SELECT * FROM products ORDER BY Price DESC;
SELECT * FROM products ORDER BY Price ASC;
```
```sql
SELECT 
 customerName,
 COUNT(*) AS 'number of orders'
FROM customers
INNER JOIN orders
 ON orders.customerID = customers.customerID
GROUP BY customers.customerID;
```
