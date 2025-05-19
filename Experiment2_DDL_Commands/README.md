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
~~~
Create a new table named contacts with the following specifications:
contact_id as INTEGER and primary key.
first_name as TEXT and not NULL.
last_name as TEXT and not NULL.
email as TEXT.
phone as TEXT and not NULL with a check constraint to ensure the length of phone is at least 10 characters.
~~~
~~~
CREATE TABLE contacts(
contact_id INTEGER PRIMARY KEY,
first_name TEXT NOT NULL,
last_name TEXT NOT NULL,
email TEXT,
phone TEXT NOT NULL CHECK(LENGTH(phone)>=10)
);
~~~

**Output:**

![Screenshot 2025-04-30 153453](https://github.com/user-attachments/assets/b251f3e5-0898-4da4-b02a-9fd834533c03)


**Question 2**
~~~
Insert all students from Archived_students table into the Student_details table.

cid         name        type        notnull     dflt_value  pk
----------  ----------  ----------  ----------  ----------  ----------
0           RollNo      INT           0                       1
1           Name        VARCHAR(100)  0                       0
2           Gender      VARCHAR(10)   0                       0
3           Subject     VARCHAR(50)   0                       0
4           MARKS       INT           0                       0
~~~
~~~
INSERT INTO Student_details(RollNo , Name, Gender, Subject, MARKS)
SELECT RollNo, Name, Gender, Subject, MARKS FROM Archived_students ;
~~~
**Output:**

![Screenshot 2025-04-30 153722](https://github.com/user-attachments/assets/b38e1d4e-6fd4-44dd-92a5-cb704e5c0500)


**Question 3**
~~~
Create a table named Invoices with the following constraints:
InvoiceID as INTEGER should be the primary key.
InvoiceDate as DATE.
Amount as REAL should be greater than 0.
DueDate as DATE should be greater than the InvoiceDate.
OrderID as INTEGER should be a foreign key referencing Orders(OrderID).
~~~
~~~
CREATE TABLE Invoices (
InvoiceID INTEGER PRIMARY KEY,
InvoiceDate DATE,
Amount REAL CHECK (Amount > 0),
DueDate DATE CHECK (DueDate > InvoiceDate),
OrderID INTEGER,
FOREIGN KEY (OrderId) REFERENCES Orders (OrderId)
);
~~~
**Output:**

![Screenshot 2025-04-30 154003](https://github.com/user-attachments/assets/1b582272-bfc6-4c40-9814-4da055277eea)


**Question 4**
~~~
Create a new table named orders with the following specifications:
ord_id as TEXT with a length of 4.
item_id as TEXT.
ord_date as DATE.
ord_qty as INTEGER.
cost as INTEGER.
The primary key is a composite key consisting of item_id and ord_date.
ord_id and item_id should not accept NULL
~~~
~~~
CREATE TABLE orders(
ord_id TEXT CHECK(Length(ord_id) = 4),
item_id TEXT NOT NULL,
ord_date  DATE NOT NULL,
ord_qty INTEGER,
cost INTEGER,
PRIMARY KEY(item_id, ord_date)
);
~~~
**Output:**

![image](https://github.com/user-attachments/assets/260c0acc-56a8-408f-9abc-76b9cf1e0442)

**Question 5**
~~~
Write a SQL query to Add a new column State as text in the Student_details table.

Sample table: Student_details

 cid              name             type   notnull     dflt_value  pk
---------------  ---------------  -----  ----------  ----------  ----------
0                RollNo           int    0                       1
1                Name             VARCH  1                       0
2                Gender           TEXT   1                       0
3                Subject          VARCH  0                       0
4                MARKS            INT (  0                       0
~~~
~~~
ALTER TABLE Student_details
ADD COLUMN State TEXT;
~~~
**Output:**

![Screenshot 2025-04-30 154241](https://github.com/user-attachments/assets/7d729356-ac3b-4413-a044-5da9238dd0e8)


**Question 6**
~~~
Create a table named Tasks with the following columns:

TaskID as INTEGER
TaskName as TEXT
DueDate as DATE
~~~
~~~
CREATE TABLE Tasks(
TaskID INTEGER,
TaskName TEXT,
DueDate DATE
);
~~~

**Output:**

![Screenshot 2025-04-30 154432](https://github.com/user-attachments/assets/d115c834-32b0-4945-a627-763eb9fe6100)

**Question 7**
~~~
Create a table named Orders with the following constraints:
OrderID as INTEGER should be the primary key.
OrderDate as DATE should be not NULL.
CustomerID as INTEGER should be a foreign key referencing Customers(CustomerID).
~~~
~~~
CREATE TABLE Orders(
OrderID INTEGER PRIMARY KEY,
OrderDate DATE NOT NULL,
CustomerID INTEGER,
FOREIGN KEY (CustomerID) REFERENCES Customers(CustomerID)
);
~~~

**Output:**

![![Screenshot 2025-04-30 154608](https://github.com/user-attachments/assets/4a7921ac-6b1f-47ab-9c0b-547beb8f4b95)


**Question 8**
Insert a new product with ProductID 101, Name Laptop, Category Electronics, Price 1500, and Stock 50 into the Products table.
~~~
INSERT INTO Products( ProductID, Name, Category, Price, Stock)
VALUES(101,'Laptop','Electronics',1500,50);
~~~

**Output:**

![Screenshot 2025-04-30 154715](https://github.com/user-attachments/assets/6d711701-ba93-4bf3-8f94-7c0cbb1fcba4)


**Question 9**
Write an SQL command can to add a column named email of type TEXT to the customers table
~~~
ALTER TABLE customers
ADD COLUMN email TEXT;
~~~

**Output:**

![Screenshot 2025-04-30 154850](https://github.com/user-attachments/assets/5f27e656-215e-4303-80ee-9aa004870ef7)


**Question 10**
~~~
Write a SQL query to Add a new column Country as text in the Student_details table.

Sample table: Student_details

 cid              name             type   notnull     dflt_value  pk
---------------  ---------------  -----  ----------  ----------  ----------
0                RollNo           int    0                       1
1                Name             VARCH  1                       0
2                Gender           TEXT   1                       0
3                Subject          VARCH  0                       0
4                MARKS            INT (  0                       0
~~~
~~~
ALTER TABLE Student_details
ADD COLUMN Country TEXT;
~~~
**Output:**

![Screenshot 2025-04-30 155059](https://github.com/user-attachments/assets/ed65cb55-f2e3-4811-a17e-496be089eb13)



## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
