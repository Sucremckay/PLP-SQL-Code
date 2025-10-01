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



‎--Database-wk-8-Assignment: Qst1
‎
‎-- Create the database
‎CREATE DATABASE LibraryManagementSystem;
‎
‎USE LibraryManagementSystem;
‎
‎-- Create Authors Table
‎CREATE TABLE Authors (
‎    AuthorID INT AUTO_INCREMENT PRIMARY KEY,
‎    AuthorName VARCHAR(255) NOT NULL,
‎    Bio TEXT
‎);
‎
‎-- Create Categories Table
‎CREATE TABLE Categories (
‎    CategoryID INT AUTO_INCREMENT PRIMARY KEY,
‎    CategoryName VARCHAR(100) NOT NULL UNIQUE
‎);
‎
‎-- Create Books Table
‎CREATE TABLE Books (
‎    BookID INT AUTO_INCREMENT PRIMARY KEY,
‎    Title VARCHAR(255) NOT NULL,
‎    AuthorID INT,
‎    CategoryID INT,
‎    ISBN VARCHAR(20) UNIQUE NOT NULL,
‎    AvailableCopies INT NOT NULL CHECK (AvailableCopies >= 0),
‎    FOREIGN KEY (AuthorID) REFERENCES Authors(AuthorID),
‎    FOREIGN KEY (CategoryID) REFERENCES Categories(CategoryID)
‎);
‎
‎-- Create Members Table
‎CREATE TABLE Members (
‎    MemberID INT AUTO_INCREMENT PRIMARY KEY,
‎    MemberName VARCHAR(255) NOT NULL,
‎    Email VARCHAR(100) UNIQUE NOT NULL,
‎    Phone VARCHAR(20),
‎    JoinDate DATE DEFAULT CURRENT_DATE
‎);
‎
‎-- Create Transactions Table
‎CREATE TABLE Transactions (
‎    TransactionID INT AUTO_INCREMENT PRIMARY KEY,
‎    MemberID INT,
‎    BookID INT,
‎    BorrowDate DATE NOT NULL,
‎    ReturnDate DATE,
‎    Status ENUM('Borrowed', 'Returned') DEFAULT 'Borrowed',
‎    FOREIGN KEY (MemberID) REFERENCES Members(MemberID),
‎    FOREIGN KEY (BookID) REFERENCES Books(BookID)
‎);
‎
‎-- Sample Insert Data
‎
‎-- Insert Authors
‎INSERT INTO Authors (AuthorName, Bio) VALUES
‎('J.K. Rowling', 'British author, known for Harry Potter series.'),
‎('George Orwell', 'English novelist and essayist, known for Animal Farm and 1984.');
‎
‎-- Insert Categories
‎INSERT INTO Categories (CategoryName) VALUES
‎('Fiction'),
‎('Non-Fiction'),
‎('Science Fiction'),
‎('Fantasy');
‎
‎-- Insert Books
‎INSERT INTO Books (Title, AuthorID, CategoryID, ISBN, AvailableCopies) VALUES
‎('Harry Potter and the Philosopher\'s Stone', 1, 4, '978-0747532743', 10),
‎('1984', 2, 2, '978-0451524935', 5);
‎
‎-- Insert Members
‎INSERT INTO Members (MemberName, Email, Phone) VALUES
‎('Alice Johnson', 'alice.johnson@email.com', '1234567890'),
‎('Bob Smith', 'bob.smith@email.com', '0987654321');
‎
‎-- Insert Transactions
‎INSERT INTO Transactions (MemberID, BookID, BorrowDate, Status) VALUES
‎(1, 1, '2025-10-01', 'Borrowed'),
‎(2, 2, '2025-10-02', 'Borrowed');
‎
‎
‎--Database-wk-8-Assignment: Qst2
‎
‎
‎--Step1: Create a New Directory for the LibraryManagementSystem
‎
‎mkdir library-crud-api
‎cd library-crud-api
‎
‎
‎--Initialize a Node.js Project:
‎
‎npm init -y
‎
‎--Step 2: Define the Database Schema
‎
‎--Create the Sequelize Model Files: Create a models directory in your project.
‎Inside the models directory, create files for Books and Members models.
‎
‎File: models/index.js (for Sequelize setup):
‎
‎const { Sequelize, DataTypes } = require('sequelize');
‎
‎// Set up the connection to the database
‎const sequelize = new Sequelize('LibraryManagementSystem', 'root', 'password', {
‎  host: 'localhost',
‎  dialect: 'mysql',
‎});
‎
‎const db = {};
‎
‎// Import models
‎db.Sequelize = Sequelize;
‎db.sequelize = sequelize;
‎
‎// Define Books Model
‎db.Book = sequelize.define('Book', {
‎  BookID: {
‎    type: DataTypes.INTEGER,
‎    primaryKey: true,
‎    autoIncrement: true,
‎  },
‎  Title: {
‎    type: DataTypes.STRING,
‎    allowNull: false,
‎  },
‎  ISBN: {
‎    type: DataTypes.STRING,
‎    unique: true,
‎    allowNull: false,
‎  },
‎  AvailableCopies: {
‎    type: DataTypes.INTEGER,
‎    allowNull: false,
‎  },
‎});
‎
‎// Define Members Model
‎db.Member = sequelize.define('Member', {
‎  MemberID: {
‎    type: DataTypes.INTEGER,
‎    primaryKey: true,
‎    autoIncrement: true,
‎  },
‎  MemberName: {
‎    type: DataTypes.STRING,
‎    allowNull: false,
‎  },
‎  Email: {
‎    type: DataTypes.STRING,
‎    unique: true,
‎    allowNull: false,
‎  },
‎});
‎
‎// Sync models with database
‎db.sequelize.sync();
‎
‎module.exports = db;
‎
‎--Step 3: Set Up Express Server
‎
‎--Create the Server File:
‎
‎File: server.js:
‎
‎const express = require('express');
‎const bodyParser = require('body-parser');
‎const db = require('./models');
‎
‎const app = express();
‎const PORT = 3000;
‎
‎// Middleware to parse JSON bodies
‎app.use(bodyParser.json());
‎
‎// CRUD Routes for Books
‎
‎// Create a new book
‎app.post('/books', async (req, res) => {
‎  try {
‎    const book = await db.Book.create(req.body);
‎    res.status(201).json(book);
‎  } catch (err) {
‎    res.status(400).json({ error: err.message });
‎  }
‎});
‎
‎// Read all books
‎app.get('/books', async (req, res) => {
‎  try {
‎    const books = await db.Book.findAll();
‎    res.status(200).json(books);
‎  } catch (err) {
‎    res.status(400).json({ error: err.message });
‎  }
‎});
‎
‎// Update a book by ID
‎app.put('/books/:id', async (req, res) => {
‎  try {
‎    const book = await db.Book.findByPk(req.params.id);
‎    if (!book) return res.status(404).json({ error: 'Book not found' });
‎    await book.update(req.body);
‎    res.status(200).json(book);
‎  } catch (err) {
‎    res.status(400).json({ error: err.message });
‎  }
‎});
‎
‎// Delete a book by ID
‎app.delete('/books/:id', async (req, res) => {
‎  try {
‎    const book = await db.Book.findByPk(req.params.id);
‎    if (!book) return res.status(404).json({ error: 'Book not found' });
‎    await book.destroy();
‎    res.status(200).json({ message: 'Book deleted successfully' });
‎  } catch (err) {
‎    res.status(400).json({ error: err.message });
‎  }
‎});
‎
‎// CRUD Routes for Members
‎
‎// Create a new member
‎app.post('/members', async (req, res) => {
‎  try {
‎    const member = await db.Member.create(req.body);
‎    res.status(201).json(member);
‎  } catch (err) {
‎    res.status(400).json({ error: err.message });
‎  }
‎});
‎
‎// Read all members
‎app.get('/members', async (req, res) => {
‎  try {
‎    const members = await db.Member.findAll();
‎    res.status(200).json(members);
‎  } catch (err) {
‎    res.status(400).json({ error: err.message });
‎  }
‎});
‎
‎// Update a member by ID
‎app.put('/members/:id', async (req, res) => {
‎  try {
‎    const member = await db.Member.findByPk(req.params.id);
‎    if (!member) return res.status(404).json({ error: 'Member not found' });
‎    await member.update(req.body);
‎    res.status(200).json(member);
‎  } catch (err) {
‎    res.status(400).json({ error: err.message });
‎  }
‎});
‎
‎// Delete a member by ID
‎app.delete('/members/:id', async (req, res) => {
‎  try {
‎    const member = await db.Member.findByPk(req.params.id);
‎    if (!member) return res.status(404).json({ error: 'Member not found' });
‎    await member.destroy();
‎    res.status(200).json({ message: 'Member deleted successfully' });
‎  } catch (err) {
‎    res.status(400).json({ error: err.message });
‎  }
‎});
‎
‎// Start the server
‎app.listen(PORT, () => {
‎  console.log(`Server is running on port ${PORT}`);
‎});
‎
‎--Step 4: Testing the API Endpoints with Postman
‎
‎--Create a Book (POST /books):
‎
‎{
‎  "Title": "The Great Gatsby",
‎  "ISBN": "9780743273565",
‎  "AvailableCopies": 5
‎}
‎
‎--Create a Member (POST /members):
‎
‎{
‎  "MemberName": "John Doe",
‎  "Email": "john.doe@example.com"
‎}
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
‎
‎
‎
‎
