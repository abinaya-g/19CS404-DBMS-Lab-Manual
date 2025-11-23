<img width="988" height="392" alt="433733602-7e6f9751-b530-4526-9a3d-8e322e3b2e6d" src="https://github.com/user-attachments/assets/1859b1e0-0123-480b-809a-38e27efaec8f" /># Experiment 2: DDL Commands

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
-Write a SQL Query to change the name of attribute "name" to "first_name" and add mobilenumber as number ,DOB as Date in the table Companies.

```sql
 ALTER TABLE Companies
rename name to first_name;
ALTER TABLE Companies
ADD COLUMN mobilenumber number;
ALTER TABLE Companies
ADD COLUMN DOB Date;
```

**Output:**

<img width="1318" height="312" alt="image" src="https://github.com/user-attachments/assets/6e90bdb4-572c-49cf-85f7-55df7b1a593c" />


**Question 2**
---
-- Create a table named Products with the following constraints: ProductID as INTEGER should be the primary key. ProductName as TEXT should be unique and not NULL. Price as REAL should be greater than 0. StockQuantity as INTEGER should be non-negative.

```sql
 CREATE TABLE Products
(
ProductID INTEGER primary key,
ProductName TEXT UNIQUE NOT NULL,
Price REAL CHECK(Price>0),
StockQuantity INTEGER CHECK(StockQuantity>0)
);
```

**Output:**

<img width="1463" height="263" alt="image" src="https://github.com/user-attachments/assets/c5a6e6ef-d14d-49a9-8a08-ee212a1c5b84" />

**Question 3**
---
-- Create a table named Products with the following columns:

ProductID as INTEGER ProductName as TEXT Price as REAL Stock as INTEGER

```sql
CREATE TABLE Products
(
ProductID INTEGER,
ProductName TEXT,
Price REAL,
Stock INTEGER
);
```

**Output:**

<img width="1678" height="306" alt="image" src="https://github.com/user-attachments/assets/a4af7410-fea5-4d66-9103-24379c8fe98b" />

**Question 4**
 Insert the following employees into the Employee table:

EmployeeID Name Position Department Salary
```

```sql
INSERT INTO Employee(EmployeeID,Name,Position,Department ,Salary)
values(2,           'John Smith'  ,'Developer'  , 'IT'  ,        75000);
INSERT INTO Employee(EmployeeID,Name,Position,Department ,Salary)
values(3,           'Anna Bell'  ,'Designer'  , 'Marketing'  ,        68000);
```

**Output:**

<img width="1571" height="347" alt="image" src="https://github.com/user-attachments/assets/91f437be-825c-409d-8b2a-52675171ebcd" />


**Question 5**
---
Create a table named Departments with the following columns:

DepartmentID as INTEGER DepartmentName as TEXT
```sql
CREATE TABLE Departments
(
DepartmentID INTEGER,
DepartmentName TEXT

);
```

**Output:**
<img width="1562" height="341" alt="image" src="https://github.com/user-attachments/assets/4414c75d-48bb-46d4-b155-6a68f5af0322" />


**Question 6**
---
--  Insert the below data into the Employee table, allowing the Department and Salary columns to take their default values.

EmployeeID Name Position

```sql
--INSERT INTO Employee(EmployeeID,Name,Position)
values(4           ,'Emily White','Analyst');
```

**Output:**
<img width="1347" height="390" alt="image" src="https://github.com/user-attachments/assets/5b892702-8b7c-4f2e-8f4a-516fd86e159a" />


**Question 7**
---
-- Create a table named Orders with the following constraints: OrderID as INTEGER should be the primary key. OrderDate as DATE should be not NULL. CustomerID as INTEGER should be a foreign key referencing Customers(CustomerID).

```sql
-- CREATE TABLE Orders
(
OrderID INTEGER primary key,
OrderDate DATE NOT NULL,
CustomerID INTEGER,
FOREIGN KEY(CustomerID) REFERENCES Customers(CustomerID)
);

```

**Output:**

<img width="1341" height="355" alt="image" src="https://github.com/user-attachments/assets/c54c6c03-f9f2-4445-a166-e5b8531e7369" />


**Question 8**
---
-- Insert the following students into the Student_details table: RollNo Name Gender Subject MARKS

```sql
-- INSERT INTO Student_details(RollNo ,Name    ,    Gender  ,    Subject ,    MARKS)
values(202       ,  'Ella King'  ,'F','Chemistry' ,  87);
INSERT INTO Student_details(RollNo ,Name    ,    Gender  ,    Subject ,    MARKS)
values(203       ,  'James Bond'  ,'M','Literature' ,  78);
```

**Output:**
<img width="1507" height="232" alt="image" src="https://github.com/user-attachments/assets/5f2fc0ca-8d32-416d-8b03-6352a632c967" />


**Question 9**
---
-- Create a new table named item with the following specifications and constraints: item_id as TEXT and as primary key. item_desc as TEXT. rate as INTEGER. icom_id as TEXT with a length of 4. icom_id is a foreign key referencing com_id in the company table. The foreign key should cascade updates and deletes. item_desc and rate should not accept NULL.

```sql
-- CREATE TABLE item
(
item_id TEXT primary key,
item_desc TEXT not null,
rate INTEGER not null,
icom_id TEXT(4),
FOREIGN KEY(icom_id) REFERENCES company(com_id)
on update cascade
on delete cascade
);
```

**Output:**

<img width="1502" height="322" alt="image" src="https://github.com/user-attachments/assets/8b315d7f-0536-4cc2-b5b9-cf7e46037d59" />


**Question 10**
---
-- Write an SQL query to add two new columns, designation and net_salary, to the table Companies. The designation column should have a data type of varchar(50), and the net_salary column should have a data type of number.

```sql
--ALTER TABLE Companies
ADD COLUMN designation varchar(50);
ALTER TABLE Companies
ADD COLUMN net_salary number;
```

**Output:**

<img width="1503" height="370" alt="image" src="https://github.com/user-attachments/assets/e5bbf311-3dd2-4b1e-9571-27784193953b" />



## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
