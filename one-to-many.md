# one-to-many

join
```sql
SELECT * FROM customers WHERE last_name = 'George';
SELECT * FROM orders WHERE customer_id = 1;

SELECT * FROM orders WHERE customer_id =
(
  SELECT id FROM customers
  WHERE last_name = 'George'
);

SELECT * FROM customers, orders;

-- IMPLICIT INNER JOIN
SELECT * FROM customers, orders WHERE customers.id = orders.customer_id;

SELECT first_name, last_name, order_date, amount FROM customers, orders WHERE customers.id = orders.customer_id;

-- EXPLICIT INNER JOIN

SELECT * FROM customers JOIN orders ON customers.id = orders.customer_id;

SELECT first_name, last_name, order_date, amount FROM customers JOIN orders ON customers.id = orders.customer_id;

SELECT * FROM customers INNER JOIN orders ON customers.id = orders.customer_id;

-- LEFT JOIN
SELECT * FROM customers LEFT JOIN orders ON customers.id = orders.customer_id;

SELECT first_name, last_name, order_date, amount FROM customers LEFT JOIN orders ON customers.id = orders.customer_id;

SELECT first_name, 
       last_name, 
       IFNULL(SUM(amount), 0) AS total_spent 
FROM   customers 
       LEFT JOIN orders 
              ON customers.id = orders.customer_id
GROUP BY customers.id 
ORDER BY total_spent;

-- RIGHT JOIN
SELECT * FROM customers RIGHT JOIN orders ON customers.id = orders.customer_id;

DELETE FROM customers WHERE first_name = 'Boy';

```

exercise
```sql
CREATE DATABASE students_and_papers;

USE students_and_papers;

CREATE TABLE students(
    id INT AUTO_INCREMENT PRIMARY KEY,
    first_name VARCHAR(100)
);

CREATE TABLE papers(
    id INT AUTO_INCREMENT PRIMARY KEY,
    title VARCHAR(100),
    grade INT,
    student_id INT,
    FOREIGN KEY(student_id) REFERENCES students(id)
);

INSERT INTO students (first_name) VALUES 
('Caleb'), ('Samantha'), ('Raj'), ('Carlos'), ('Lisa');

INSERT INTO papers (student_id, title, grade ) VALUES
(1, 'My First Book Report', 60),
(1, 'My Second Book Report', 75),
(2, 'Russian Lit Through The Ages', 94),
(2, 'De Montaigne and The Art of The Essay', 98),
(4, 'Borges and Magical Realism', 89);

--
SELECT first_name, title, grade FROM students JOIN papers ON students.id = papers.student_id
ORDER BY grade DESC;

SELECT first_name, title, grade FROM students LEFT JOIN papers ON students.id = papers.student_id;

SELECT first_name, 
IFNULL(title, 'MISSING') AS 'title', 
IFNULL(grade, 0) AS 'grade'
FROM students LEFT JOIN papers ON students.id = papers.student_id;

SELECT first_name,
IFNULL(AVG(grade), 0) AS 'average'
FROM students LEFT JOIN papers ON students.id = papers.student_id
GROUP BY first_name ORDER BY grade DESC;

SELECT first_name, 
IFNULL(AVG(grade), 0) AS 'average',
CASE
    WHEN AVG(grade) IS NULL THEN 'FAILING'
    WHEN AVG(grade) >= 75 THEN 'PASSING'
    ELSE 'FAILING'
END AS 'passing_status'
FROM students LEFT JOIN papers ON students.id = papers.student_id
GROUP BY first_name ORDER BY grade DESC;
```
