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
<img width="1158" height="472" alt="image" src="https://github.com/user-attachments/assets/b71a4ab4-b9e0-43e5-b866-6dcd1c1b5cf0" />


```sql
INSERT INTO Student_details (RollNo, Name, Gender)
VALUES (205, 'Olivia Green', 'F');

INSERT INTO Student_details (RollNo, Name, Gender, Subject, MARKS)
VALUES (207, 'Liam Smith', 'M', 'Mathematics', 85);

INSERT INTO Student_details (RollNo, Name, Gender, Subject)
VALUES (208, 'Sophia Johnson', 'F', 'Science');
```

**Output:**

<img width="1222" height="356" alt="image" src="https://github.com/user-attachments/assets/5a64a231-a599-4e0a-97be-5143d581ae33" />


**Question 2**
---
<img width="1218" height="398" alt="image" src="https://github.com/user-attachments/assets/15025444-8ebd-47ab-ba3a-2cb91995e06e" />


```sql
CREATE table Products(
ProductID INTEGER primary key,
ProductName TEXT unique not NULL,
Price REAL check(Price>0),
StockQuantity INTEGER check(StockQuantity>=0)
);
```

**Output:**

<img width="1214" height="346" alt="image" src="https://github.com/user-attachments/assets/dafa86f3-d034-4351-ac7c-27fbe3e5bd5b" />


**Question 3**
---
<img width="1179" height="580" alt="image" src="https://github.com/user-attachments/assets/f0e3de2b-cf9f-4aeb-a021-5514d77bafa8" />


```sql
ALTER table customer ADD column email VARCHAR(100);
```

**Output:**

<img width="1220" height="423" alt="image" src="https://github.com/user-attachments/assets/904d431a-89ee-4424-a709-250f8e2ea3e7" />


**Question 4**
---
<img width="1213" height="425" alt="image" src="https://github.com/user-attachments/assets/9b6ed96b-24de-4ad8-8191-c08c3b6bbcd8" />


```sql
CREATE table Employees(
EmployeeID INTEGER primary key,
FirstName TEXT NOT NULL,
LastName TEXT NOT NULL,
Email TEXT unique,
Salary REAL check(Salary>0),
DepartmentID INTEGER,
FOREIGN KEY (DepartmentID) REFERENCES Departments(DepartmentID)
);
```

**Output:**

<img width="1215" height="495" alt="image" src="https://github.com/user-attachments/assets/42536084-556a-4adf-a25a-a8a188388e58" />


**Question 5**
---
<img width="778" height="347" alt="image" src="https://github.com/user-attachments/assets/16f72775-35d2-486b-9167-132f1d7b93df" />


```sql
CREATE table Products(
ProductID INTEGER primary key,
ProductName TEXT NOT NULL,
Price REAL check(Price>0),
Stock INTEGER check(Stock>=0)
);
```

**Output:**

<img width="1217" height="338" alt="image" src="https://github.com/user-attachments/assets/d3d968a9-ab92-4967-9ef0-7eb62e82fd26" />


**Question 6**
---
<img width="1192" height="270" alt="image" src="https://github.com/user-attachments/assets/3db4dc81-c8f9-4d26-9c07-ed3489aee07e" />


```sql
INSERT into Products(ProductID,Name,Category)
values(104,'Tablet','Electronics');
```

**Output:**

<img width="1216" height="310" alt="image" src="https://github.com/user-attachments/assets/cacf507c-0679-4834-92b1-fa8d2acdb351" />


**Question 7**
---
<img width="1213" height="353" alt="image" src="https://github.com/user-attachments/assets/6bc0e6ab-38ff-4062-b23e-44b4f70b44d6" />


```sql
CREATE table Shipments(
ShipmentID INTEGER primary key,
ShipmentDate DATE,
SupplierID INTEGER,
ORDERID INTEGER,
FOREIGN KEY (SupplierID) REFERENCES Suppliers(SupplierID),
FOREIGN KEY (OrderID) REFERENCES Orders(OrderID)
);
```

**Output:**

<img width="1216" height="317" alt="image" src="https://github.com/user-attachments/assets/8e7c00a9-171a-4091-ab33-8e9ab6a67a98" />


**Question 8**
---
<img width="1166" height="340" alt="image" src="https://github.com/user-attachments/assets/2e8fd9ae-174b-473d-8898-178e66fba547" />


```sql
ALTER TABLE Student_details
ADD COLUMN email TEXT NOT NULL DEFAULT 'Invalid';
```

**Output:**

<img width="1213" height="306" alt="image" src="https://github.com/user-attachments/assets/0652e6c1-b444-47d4-a6b1-08ae5a03a3c5" />


**Question 9**
---
<img width="877" height="337" alt="image" src="https://github.com/user-attachments/assets/bae4c2a3-2a79-43d6-a92d-15c90d8b5c43" />


```sql
INSERT into customers(CustomerID, Name, Address, Email)
SELECT  CustomerID, Name, Address, Email
FROM old_customers;
```

**Output:**

<img width="1218" height="371" alt="image" src="https://github.com/user-attachments/assets/c51b757d-776b-4fa6-8df8-7ff47c567e16" />


**Question 10**
---
<img width="1028" height="392" alt="image" src="https://github.com/user-attachments/assets/cf3fea97-4944-45f0-850a-6bf01f35986d" />


```sql
CREATE table Locations(
LocationID INTEGER,
LocationName TEXT,
Address TEXT);
```

**Output:**

<img width="1209" height="454" alt="image" src="https://github.com/user-attachments/assets/1f9b5231-403b-471f-b6b8-aaaad9ccc064" />



## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
