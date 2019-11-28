# mysql-course

Start mysql server
```bash
docker-compose up -d
```

Get inside mysql 
```bash
docker exec -it mysql mysql -u root -ppassword
```

Stop mysql server
```bash
docker-compose down
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
