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
