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
Create a table named Products with the following columns:

ProductID as INTEGER ProductName as TEXT Price as REAL Stock as INTEGER

Syntax:
```sql
CREATE TABLE Table_Name (
  col_name1 data_type,
  col_name2 data_type,
  col_name3 data_type DEFAULT 'default_value'
);
```

**Question 1**
```
CREATE TABLE Products(
ProductID INTEGER,
ProductName TEXT,
Price REAL,
Stock INTEGER
);


```

**Output:**

<img width="1266" height="352" alt="image" src="https://github.com/user-attachments/assets/c3c8cb04-750a-4828-a1a9-b6ef8fad99a5" />


**Question 2**
Insert all customers from Old_customers into Customers

Table attributes are CustomerID, Name, Address, Email
```
INSERT INTO Customers(CustomerID, Name, Address, Email)
SELECT CustomerID, Name, Address, Email
FROM Old_customers
```

**Output:**

<img width="1262" height="287" alt="image" src="https://github.com/user-attachments/assets/b02e6616-b5fa-4c38-85df-13b3cac3be28" />

**Question 3**
Write a SQL query to Add a new ParentsNumber column as number and Adhar_Number as Number in the Student_details table.
```
ALTER TABLE Student_details ADD ParentsNumber number;
ALTER TABLE Student_details ADD Adhar_Number number;


```

**Output:**

<img width="1257" height="290" alt="image" src="https://github.com/user-attachments/assets/d515cf06-8534-4197-8f8d-5a6b616fb1a1" />


**Question 4**
Write a SQL query to Add a new column Country as text in the Student_details table.
```
ALTER TABLE Student_details ADD ParentsNumber number;
ALTER TABLE Student_details ADD Adhar_Number number;
```

**Output:**

<img width="1257" height="395" alt="image" src="https://github.com/user-attachments/assets/60cb5be4-8754-4dfe-811b-d23f58679c93" />


**Question 5**
---
Create a table named Attendance with the following constraints: AttendanceID as INTEGER should be the primary key. EmployeeID as INTEGER should be a foreign key referencing Employees(EmployeeID). AttendanceDate as DATE. Status as TEXT should be one of 'Present', 'Absent', 'Leave'.
```
CREATE TABLE Attendance(
AttendanceID INTEGER PRIMARY KEY,
EmployeeID INTEGER,
AttendanceDate DATE,
Status TEXT CHECK (Status IN('Present','Absent','Leave')),
FOREIGN KEY (EmployeeID) REFERENCES Employees(EmployeeID)
);
```
**Output:**

<img width="1262" height="287" alt="image" src="https://github.com/user-attachments/assets/ff023132-280d-4f96-aceb-082ac0c0682d" />


**Question 6**
---
Insert a product with ProductID 104, Name Tablet, and Category Electronics into the Products table, where Price and Stock should use default values.
```
INSERT INTO Products (ProductID,Name,Category)
VALUES(104,'Tablet','Electronics');
```
**Output:**

<img width="1262" height="262" alt="image" src="https://github.com/user-attachments/assets/7d502d44-9d7c-4839-8081-e698eebe2296" />


**Question 7**
---
Create a table named Tasks with the following columns:

TaskID as INTEGER TaskName as TEXT DueDate as DATE
```
CREATE TABLE Tasks(
TaskID INTEGER,
TaskName TEXT,
DueDate DATE
);
```

**Output:**

<img width="1262" height="382" alt="image" src="https://github.com/user-attachments/assets/ce9f0934-79d0-4d13-82d1-011ce59cc33c" />


**Question 8**
---
Insert a new product with ProductID 101, Name Laptop, Category Electronics, Price 1500, and Stock 50 into the Products table.
```
INSERT INTO Products (ProductID,Name,Category,Price,Stock)
VALUES(101,'Laptop','Electronics',1500,50);
```

**Output:**

<img width="1257" height="231" alt="image" src="https://github.com/user-attachments/assets/5d07660d-7b89-4ea0-a5b3-5e0a2de5f624" />


**Question 9**
Create a table named Shipments with the following constraints: ShipmentID as INTEGER should be the primary key. ShipmentDate as DATE. SupplierID as INTEGER should be a foreign key referencing Suppliers(SupplierID). OrderID as INTEGER should be a foreign key referencing Orders(OrderID).
```
CREATE TABLE Shipments(
ShipmentID INTEGER PRIMARY KEY,
ShipmentDate DATE,
SupplierID INTEGER,
OrderId INTEGER,
FOREIGN KEY (SupplierID) REFERENCES Suppliers(SupplierId),
FOREIGN KEY (OrderId)REFERENCES Orders(OrderID)

);
```

**Output:**

<img width="1257" height="231" alt="image" src="https://github.com/user-attachments/assets/e3d7a8fb-b1b2-459c-a1c0-cc7dd8f43871" />

**Question 10**
Create a table named Bonuses with the following constraints: BonusID as INTEGER should be the primary key. EmployeeID as INTEGER should be a foreign key referencing Employees(EmployeeID). BonusAmount as REAL should be greater than 0. BonusDate as DATE. Reason as TEXT should not be NULL.
```
CREATE TABLE Bonuses(
BonusID INTEGER PRIMARY KEY,
EmployeeID INTEGER,
BonusAmount REAL CHECK (BonusAmount>0),
BonusDate DATE,
Reason TEXT NOT NULL,
FOREIGN KEY (EmployeeID)REFERENCES
Employees(EmployeeID)
);
```

**Output:**
<img width="1277" height="270" alt="image" src="https://github.com/user-attachments/assets/1b0211a7-2af7-4b4b-b9b0-15445c5354ad" />


## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
