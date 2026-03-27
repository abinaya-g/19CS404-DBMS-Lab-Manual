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
--
Create a table named Employees with the following columns:

EmployeeID as INTEGER
FirstName as TEXT
LastName as TEXT
HireDate as DATE
```sql
CREATE TABLE Employees
(
EmployeeID INTEGER,
FirstName TEXT,
LastName TEXT,
HireDate DATE
);
```

**Output:**
<img width="1225" height="379" alt="image" src="https://github.com/user-attachments/assets/8d5df310-3892-4346-ae9e-fb531442b211" />



**Question 2**
---
Insert all employees from Former_employees into Employee

Table attributes are EmployeeID, Name, Department, Salary

```sql
INSERT INTO Employee select EmployeeID,Name,Department,Salary from Former_employees
```

**Output:**
<img width="1218" height="336" alt="image" src="https://github.com/user-attachments/assets/bd10f719-d37f-435e-889f-30ac3fa68bfc" />


**Question 3**
---
Create a table named ProjectAssignments with the following constraints:
AssignmentID as INTEGER should be the primary key.
EmployeeID as INTEGER should be a foreign key referencing Employees(EmployeeID).
ProjectID as INTEGER should be a foreign key referencing Projects(ProjectID).
AssignmentDate as DATE should be NOT NULL.

```sql
CREATE TABLE ProjectAssignments
(
AssignmentID INTEGER primary key,
EmployeeID INTEGER,
ProjectID INTEGER,
AssignmentDate DATE not null,
foreign key (EmployeeID) references Employees(EmployeeID),
foreign key (ProjectID) references Projects(ProjectID)
);
```

**Output:**

<img width="1223" height="343" alt="image" src="https://github.com/user-attachments/assets/5817421b-2d9d-42a3-906c-bc5a75e75722" />


**Question 4**
---
Insert a new product with ProductID 101, Name Laptop, Category Electronics, Price 1500, and Stock 50 into the Products table.

```sql
INSERT INTO Products(ProductID,Name,Category,Price,Stock) Values(101,"Laptop","Electronics",1500,50)
```

**Output:**
<img width="1208" height="314" alt="image" src="https://github.com/user-attachments/assets/a9b10893-6c94-4648-a2f3-18652c9d367d" />


**Question 5**
---
Create a table named Products with the following constraints:
ProductID as INTEGER should be the primary key.
ProductName as TEXT should be unique and not NULL.
Price as REAL should be greater than 0.
StockQuantity as INTEGER should be non-negative.
```sql
CREATE TABLE Products
(
ProductID INT primary key,
ProductName TEXT UNIQUE not null,
Price REAL check(Price >0),
StockQuantity INT check(StockQuantity >0)
);
```

**Output:**

<img width="1213" height="355" alt="image" src="https://github.com/user-attachments/assets/039a871f-c2e5-4ca6-a39a-e40a0f47b511" />


**Question 6**
---
In the Student_details table, insert a student record where some fields are NULL, another record where all fields are filled without any NULL values, and a third record where some fields are filled, and others are left as NULL.

RollNo      Name            Gender      Subject      MARKS
----------  ------------    ----------  ----------   ----------
205         Olivia Green    F
207         Liam Smith      M           Mathematics  85
208         Sophia Johnson  F           Science

```sql
INSERT INTO Student_details(RollNO,Name,Gender,Subject,Marks)
VALUES(205,"Olivia Green","F",null,null),
(207,"Liam Smith","M","Mathematics",85),
(208,"Sophia Johnson","F","Science",null)
```

**Output:**
<img width="1214" height="352" alt="image" src="https://github.com/user-attachments/assets/30a2d73c-430e-4c79-bea0-d21236b6f86c" />



**Question 7**
---
Create a table named Employees with the following constraints:

EmployeeID should be the primary key.
FirstName and LastName should be NOT NULL.
Email should be unique.
Salary should be greater than 0.
DepartmentID should be a foreign key referencing the Departments table.
```sql
CREATE TABLE Employees
(
EmployeeID INT primary key,
FirstName TEXT not null,
lastName TEXT not null,
Email TEXT UNIQUE,
Salary INT check(Salary>0),
DepartmentID INT,
foreign key (DepartmentID) references Departments(DepartmentID)
);
```

**Output:**
<img width="1213" height="494" alt="image" src="https://github.com/user-attachments/assets/df9f9a70-947c-450b-bc54-0b707806067c" />



**Question 8**
---
Write a SQL Query  to change the name of attribute "name" to "first_name"  and add mobilenumber as number ,DOB as Date in the table Companies. 

```sql
alter table Companies
rename name to first_name;
alter table Companies
add mobilenumber number;
alter table Companies
add DOB Date;
```

**Output:**
<img width="1222" height="462" alt="image" src="https://github.com/user-attachments/assets/eecb45ad-a2ef-4bc5-948d-95914094d866" />


**Question 9**
---
Write an SQL query to add two new columns, first_name and last_name, to the table employee. Both columns should have a data type of varchar(50).

```sql
ALTER TABLE employee
add first_name varchar(50);
ALTER TABLE employee
add last_name varchar(50);
```

**Output:**
<img width="1221" height="381" alt="image" src="https://github.com/user-attachments/assets/50d840fe-667f-4a10-ba13-d7470253155f" />


**Question 10**
---
Create a table named Invoices with the following constraints:

InvoiceID as INTEGER should be the primary key.
InvoiceDate as DATE.
DueDate as DATE should be greater than the InvoiceDate.
Amount as REAL should be greater than 0.

```sql
create table Invoices
(
InvoiceID INT primary key,
InvoiceDate Date,
DueDate DATE check(DueDate>InvoiceDate),
Amount REAL check(Amount>0)
);
```
**Output:**
<img width="1218" height="350" alt="image" src="https://github.com/user-attachments/assets/3a0a315e-dd6a-4f01-b1e2-3583d4cc4b46" />

**GRADE:**
<img width="770" height="606" alt="image" src="https://github.com/user-attachments/assets/eb9dff6e-fafa-402f-8b9c-b54ad5b0f7c2" />



## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
