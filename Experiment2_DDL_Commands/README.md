# Experiment 2: DDL Commands

## AIM
To study and implement DDL commands and different types of constraints.

## THEORY

### 1. CREATE
Used to create a new relation (table).

**Syntax:**
```sql
CREATE TABLE (
  field_1 data_type(size),
  field_2 data_type(size),
  ...
);
```
### 2. ALTER
Used to add, modify, drop, or rename fields in an existing relation.
(a) ADD
```sql
ALTER TABLE std ADD (Address CHAR(10));
```
(b) MODIFY
```sql
ALTER TABLE relation_name MODIFY (field_1 new_data_type(size));
```
(c) DROP
```sql
ALTER TABLE relation_name DROP COLUMN field_name;
```
(d) RENAME
```sql
ALTER TABLE relation_name RENAME COLUMN old_field_name TO new_field_name;
```
### 3. DROP TABLE
Used to permanently delete the structure and data of a table.
```sql
DROP TABLE relation_name;
```
### 4. RENAME
Used to rename an existing database object.
```sql
RENAME TABLE old_relation_name TO new_relation_name;
```
### CONSTRAINTS
Constraints are used to specify rules for the data in a table. If there is any violation between the constraint and the data action, the action is aborted by the constraint. It can be specified when the table is created (using CREATE TABLE) or after it is created (using ALTER TABLE).
### 1. NOT NULL
When a column is defined as NOT NULL, it becomes mandatory to enter a value in that column.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) NOT NULL
);
```
### 2. UNIQUE
Ensures that values in a column are unique.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) UNIQUE
);
```
### 3. CHECK
Specifies a condition that each row must satisfy.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) CHECK (logical_expression)
);
```
### 4. PRIMARY KEY
Used to uniquely identify each record in a table.
Properties:
Must contain unique values.
Cannot be null.
Should contain minimal fields.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) PRIMARY KEY
);
```
### 5. FOREIGN KEY
Used to reference the primary key of another table.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size),
  FOREIGN KEY (column_name) REFERENCES other_table(column)
);
```
### 6. DEFAULT
Used to insert a default value into a column if no value is specified.

Syntax:
```sql
CREATE TABLE Table_Name (
  col_name1 data_type,
  col_name2 data_type,
  col_name3 data_type DEFAULT 'default_value'
);
```

**Question 1**

Insert all customers from Old_customers into Customers

Table attributes are CustomerID, Name, Address, Email
![image](https://github.com/user-attachments/assets/815642bf-2de1-43b3-a103-0ff687696d38)
##Query
```
INSERT INTO Customers
SELECT CustomerID, Name, Address, Email
FROM Old_customers;
```
**Output:**
![image](https://github.com/user-attachments/assets/7f3f0354-d890-480e-b5f0-e2c6c7911b60)

**Question 2**

Write a SQL query to add a new column MobileNumber of type NUMBER and a new column Address of type VARCHAR(100) to the Student_details table.
##Query
```
ALTER TABLE Student_details
ADD COLUMN MobileNumber NUMBER;
ALTER TABLE Student_details
ADD COLUMN Address VARCHAR(100);

```
**Output:**
![image](https://github.com/user-attachments/assets/0087a024-a5f3-4012-a30e-cd7ee32c0df3)



**Question 3**

Create a table named Invoices with the following constraints: InvoiceID as INTEGER should be the primary key. InvoiceDate as DATE. Amount as REAL should be greater than 0. DueDate as DATE should be greater than the InvoiceDate. OrderID as INTEGER should be a foreign key referencing Orders(OrderID).
##Query
```
CREATE TABLE Invoices(
InvoiceID INTEGER PRIMARY KEY,
InvoiceDate DATE,
Amount REAL CHECK(Amount>0),
DueDate DATE CHECK(DueDate>InvoiceDate),
OrderID INTEGER,
foreign key (OrderID) references  Orders(OrderID));
```
**Output:**

![image](https://github.com/user-attachments/assets/992bb352-390b-4b94-afac-4904505a12ce)

**Question 4**

Create a table named Employees with the following columns:

EmployeeID as INTEGER FirstName as TEXT LastName as TEXT HireDate as DATE
![image](https://github.com/user-attachments/assets/7e7e4cdd-8fd9-4bb4-8c6b-6719ad2b8b5f)

##Query
```
CREATE TABLE Employees(
EmployeeID INTEGER,
FirstName TEXT,
LastName TEXT,
HireDate DATE);
```
**Output:**

![image](https://github.com/user-attachments/assets/3274f159-5134-4344-8f47-15b1bc92dc8d)


**Question 5**

Create a table named Department with the following constraints: DepartmentID as INTEGER should be the primary key. DepartmentName as TEXT should be unique and not NULL. Location as TEXT.
##Query
```
CREATE TABLE Department(
DepartmentID INTEGER PRIMARY KEY,
DepartmentName TEXT UNIQUE NOT NULL,
Location TEXT);
```
**Output:**
![image](https://github.com/user-attachments/assets/628f7c38-c6a2-41c9-942e-66cc3f7e1e0c)


**Question 6**

Write a SQL query to add birth_date attribute as timestamp (datatype) in the table customer
![image](https://github.com/user-attachments/assets/2a129183-07c7-4274-838b-675573cbe096)
##Query
```
ALTER TABLE customer
ADD COLUMN birth_date
timestamp;
```
**Output:**

![image](https://github.com/user-attachments/assets/d92ad237-ee43-43d0-9ca4-7ce37ff5ec17)

**Question 7**

In the Student_details table, insert a student record where some fields are NULL, another record where all fields are filled without any NULL values, and a third record where some fields are filled, and others are left as NULL. 
![439126568-636acb2d-7512-4f86-9e68-52a20742a2ba](https://github.com/user-attachments/assets/d1a46498-e94e-4fa6-975d-48e0a2774f25)

##Query
```INSERT INTO Student_details(RollNo,Name,Gender,Subject,MARKS)
VALUES(205,'Olivia Green','F',NULL,NULL);
INSERT INTO Student_details(RollNo,Name,Gender,Subject,MARKS)
VALUES(207,'Liam Smith','M','Mathematics',85);
INSERT INTO Student_details(RollNo,Name,Gender,Subject,MARKS)
VALUES(208,'Sophia Johnson','F','Science',NULL);
```
**Output:**
![438791032-452b2f27-0f93-4cbd-9430-e3c307042875](https://github.com/user-attachments/assets/fe699880-628c-4d2b-af3e-335503eddda1)


**Question 8**

Create a table named Bonuses with the following constraints: BonusID as INTEGER should be the primary key. EmployeeID as INTEGER should be a foreign key referencing Employees(EmployeeID). BonusAmount as REAL should be greater than 0. BonusDate as DATE. Reason as TEXT should not be NULL.
##Query
```
CREATE TABLE Bonuses(
BonusID INTEGER PRIMARY KEY,
EmployeeID INTEGER,
BonusAmount REAL CHECK(BonusAmount>0),
BonusDate DATE,
Reason TEXT NOT NULL,
foreign key (EmployeeID) references Employees(EmployeeID));
```
**Output:**

![438791645-d4be315a-dcd6-4014-8dbc-3d61a1cb8342](https://github.com/user-attachments/assets/c25a7513-906e-4506-baf9-941f54f8a569)


**Question 9**

Create a table named Shipments with the following constraints: ShipmentID as INTEGER should be the primary key. ShipmentDate as DATE. SupplierID as INTEGER should be a foreign key referencing Suppliers(SupplierID). OrderID as INTEGER should be a foreign key referencing Orders(OrderID). For example:

Test INSERT INTO Shipments (ShipmentID, ShipmentDate, SupplierID, OrderID) VALUES (2, '2024-08-03', 99, 1); Result Error: FOREIGN KEY constraint faile
##Query
```
CREATE TABLE Shipments(
ShipmentID INTEGER PRIMARY KEY,
ShipmentDate DATE,
SupplierID INTEGER,
OrderID INTEGER,
foreign key (SupplierID) references Suppliers(SupplierID),
foreign key (OrderID) references Orders(OrderID));
```

**Output:**

![438792261-b76d1407-6b14-404e-b72e-44d419c6b968](https://github.com/user-attachments/assets/bd799265-5d05-4710-9866-1503c70ed660)


**Question 10**

Insert a book with ISBN 978-1234567890, Title Data Science Essentials, Author Jane Doe, Publisher TechBooks, and Year 2024 into the Books table.
##Query
```
INSERT INTO Books(ISBN,Title,Author,Publisher,Year)
VALUES('978-1234567890','Data Science Essentials','Jane Doe','TechBooks',2024);
```

**Output:**

![438792911-b49f81cd-8792-417a-85f9-1201b2ac69eb](https://github.com/user-attachments/assets/b1d1bd0d-f57d-4d24-9037-cd79ff198599)



## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
