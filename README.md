--PLP-SQL-Code


‎--Database-Wk-1 Assignment 
‎/*Write an SQL query to create a database called salesDB.
‎Write an SQL query to drop delete a database called Demo.*/
‎
‎--source code
‎
‎DROP DATABASE SchoolDB;
‎
‎DROP DATABASE Demo;
‎
‎
‎--Database-Wk-2 Assignment:
‎
‎USE expenses_tracker;
‎
‎SELECT *
‎FROM expenses;
‎
‎SELECT category, amount
‎FROM expenses;
‎
‎SELECT * 
‎FROM expenses
‎WHERE date BETWEEN 2023-06-05 AND 2024-07-20
‎
‎SELECT *
‎FROM expenses
‎WHERE category like '%entertainment%';
‎
‎SELECT *
‎FROM expenses
‎WHERE amount > 200
‎
‎SELECT *
‎FROM expenses
‎WHERE category like '%transportion%';
‎
‎SELECT *
‎FROM expenses
‎WHERE amount > 200 AND category like '%transportion%';
‎
‎SELECT *
‎FROM expenses
‎WHERE category NOT IN ('rent')
‎
‎SELECT *
‎FROM expenses
‎ORDER BY amount DESC;
‎
‎SELECT *
‎FROM expenses
‎ORDER BY data DESC, amount ASC;
‎
‎CREATE TABLE income
‎Income_id PRIMARY KEY, AUTO_INCREMENT
‎amount DECIMAL(10, 2) NOT NULL
‎date DATE NOT NULL
‎source VARCHAR(70) NOT NULL
‎
‎ADD TABLE income
‎ADD category VARCHAR(50);
‎
‎ALTER TABLE income
‎DROP COLUMN source;
‎
‎DROP TABLE income;
‎
‎
‎--Database-Wk-3 Assignment 
‎
‎SELECT category, SUM(amount) AS total_spent
‎FROM expenses
‎GROUP BY category;
‎
‎SELECT category, AVG(amount) AS average_spent
‎FROM expenses
‎GROUP BY category;
‎
‎SELECT category, SUM(amount) AS total_spent
‎FROM expenses
‎OREDER BY category
‎GROUP BY category DESC
‎Limit 3;
‎
‎--Database-Wk-4 Assignment
‎SELECT paymentDate
‎SUM(amount) AS totalAmount
‎FROM payment
‎ORDER BY paymentDate
‎GROUP BY paymentDate DESC
‎Limit 5;
‎
‎SELECT customerName, Country
‎AVG(creditLimit) AS average_creditLimit
‎FROM customer
‎GROUP BY customerName, Country;
‎
‎SELECT productCode, quantityOrdered
‎SUM(priceEach * quantityOrdered) AS total_price
‎FROM orderdetails
‎GROUP BY productCode, quantityOrdered;
‎
‎SELECT check number
‎MAX(amount) AS highest_Amount
‎FROM payment
‎ORDER BY check number;


‎--Database-Wk-4 Assignment
‎SELECT paymentDate
‎SUM(amount) AS totalAmount
‎FROM payment
‎ORDER BY paymentDate
‎GROUP BY paymentDate DESC
‎Limit 5;
‎
‎SELECT customerName, Country
‎AVG(creditLimit) AS average_creditLimit
‎FROM customer
‎GROUP BY customerName, Country;
‎
‎SELECT productCode, quantityOrdered
‎SUM(priceEach * quantityOrdered) AS total_price
‎FROM orderdetails
‎GROUP BY productCode, quantityOrdered;
‎
‎SELECT check number
‎MAX(amount) AS highest_Amount
‎FROM payment
‎ORDER BY check number;
‎
‎--Database-wk-5 Assignment 
‎
‎DROP INDEX  IF EXITS IDsphone ON CustomerID;
‎
‎CREATE USER 'bob@localhost' IDENTIFIED BY 'PASS123';
‎
‎GRANT INSERT ON SalesDB.* TO 'bob'@'localhost';
‎FLUSH PRIVILEGES;
‎
‎ALTER USER 'bob@localhost' IDENTIFIED BY 'PASS123';

‎
‎--Database-wk-6 Assignment
‎
‎USE salesDB;
‎
‎SELECT 
‎employees.firstName,
‎employees.lastName,
‎employees.email,
‎employees.officeCode,
‎FROM employees;
‎
‎INNER JOIN offices 
‎ON employees.officeCode = officeCode.officeCode;
‎
‎SELECT productName,
‎productName.productVendor
‎productName.productLine,
‎
‎FROM products
‎LEFT JOIN productLines
‎ON productLine = productLine.productLine;
‎
‎SELECT 
‎offices.orderDate,
‎offices.shippedDate,
‎offices.status,
‎offices.customerNumber,
‎FROM customer
‎RIGHT JOIN order 
‎ON customer.customerName = offices.customerName
‎LIMIT 10;
‎
‎
‎--Another way to write the code
‎
‎USE salesDB;
‎
‎SELECT 
‎e.firstName,
‎e.lastName,
‎e.email,
‎e.officeCode,
‎FROM employees e
‎INNER JOIN offices o
‎ON e.officeCode = o.officeCode;
‎
‎SELECT productName,
‎productName.productVendor
‎productName.productLine,
‎
‎FROM products p
‎LEFT JOIN productLines pl
‎ON p.productLine = pl.pl;
‎
‎SELECT 
‎o.orderDate,
‎o.shippedDate,
‎o.status,
‎o.customerNumber,
‎FROM customer c
‎RIGHT JOIN order o
‎ON c.customerName = o.customerName
‎LIMIT 10;
‎
‎
--Database-wk-7-Assignment

‎--Employee Salary History
‎
‎CREATE TABLE EmployeeSalaryHistory (
‎    EmployeeID INT,
‎    Salary DECIMAL(10,2),
‎    ValidFrom DATE,
‎    ValidTo DATE,
‎    TransactionStart TIMESTAMP,
‎    TransactionEnd TIMESTAMP
‎);
‎
‎--Content Management System
‎
‎CREATE TABLE Contents (
‎    ContentID INT PRIMARY KEY,
‎    Title VARCHAR(200),
‎    ContentType ENUM('Article', 'Video', 'Podcast')
‎);
‎
‎CREATE TABLE Articles (
‎    ContentID INT PRIMARY KEY,
‎    Body TEXT,
‎    FOREIGN KEY (ContentID) REFERENCES Contents(ContentID)
‎);
‎
‎CREATE TABLE Videos (
‎    ContentID INT PRIMARY KEY,
‎    URL VARCHAR(255),
‎    Duration INT,
‎    FOREIGN KEY (ContentID) REFERENCES Contents(ContentID)
‎);
‎
‎
‎
‎
‎
‎
‎
‎
‎
‎
‎
‎
‎
‎
‎
‎
‎
‎
‎
‎
‎
‎
‎
‎
‎
‎
‎
‎
‎
‎
‎
‎
‎
‎
‎
‎
‎
‎
‎
