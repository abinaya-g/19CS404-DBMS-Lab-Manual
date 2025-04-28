# Experiment 2: DDL Commands

## AIM
To study and implement DDL commands and different types of constraints.

## THEORY

### 1. CREATE
Used to create a new relation (table).

*Syntax:*
sql
CREATE TABLE (
  field_1 data_type(size),
  field_2 data_type(size),
  ...
);

### 2. ALTER
Used to add, modify, drop, or rename fields in an existing relation.
(a) ADD
sql
ALTER TABLE std ADD (Address CHAR(10));

(b) MODIFY
sql
ALTER TABLE relation_name MODIFY (field_1 new_data_type(size));

(c) DROP
sql
ALTER TABLE relation_name DROP COLUMN field_name;

(d) RENAME
sql
ALTER TABLE relation_name RENAME COLUMN old_field_name TO new_field_name;

### 3. DROP TABLE
Used to permanently delete the structure and data of a table.
sql
DROP TABLE relation_name;

### 4. RENAME
Used to rename an existing database object.
sql
RENAME TABLE old_relation_name TO new_relation_name;

### CONSTRAINTS
Constraints are used to specify rules for the data in a table. If there is any violation between the constraint and the data action, the action is aborted by the constraint. It can be specified when the table is created (using CREATE TABLE) or after it is created (using ALTER TABLE).
### 1. NOT NULL
When a column is defined as NOT NULL, it becomes mandatory to enter a value in that column.
Syntax:
sql
CREATE TABLE Table_Name (
  column_name data_type(size) NOT NULL
);

### 2. UNIQUE
Ensures that values in a column are unique.
Syntax:
sql
CREATE TABLE Table_Name (
  column_name data_type(size) UNIQUE
);

### 3. CHECK
Specifies a condition that each row must satisfy.
Syntax:
sql
CREATE TABLE Table_Name (
  column_name data_type(size) CHECK (logical_expression)
);

### 4. PRIMARY KEY
Used to uniquely identify each record in a table.
Properties:
Must contain unique values.
Cannot be null.
Should contain minimal fields.
Syntax:
sql
CREATE TABLE Table_Name (
  column_name data_type(size) PRIMARY KEY
);

### 5. FOREIGN KEY
Used to reference the primary key of another table.
Syntax:
sql
CREATE TABLE Table_Name (
  column_name data_type(size),
  FOREIGN KEY (column_name) REFERENCES other_table(column)
);

### 6. DEFAULT
Used to insert a default value into a column if no value is specified.

Syntax:
sql
CREATE TABLE Table_Name (
  col_name1 data_type,
  col_name2 data_type,
  col_name3 data_type DEFAULT 'default_value'
);


*Question 1*
--
-- Insert all products from Discontinued_products into Products.

Table attributes are ProductID, ProductName, Price, Stock
sql

```
INSERT INTO Products(ProductID,ProductName,Price,Stock)
select productID,ProductName,Price,Stock
from Discontinued_products;
```

*Output:*

![image](https://github.com/user-attachments/assets/9d4b93d5-eac4-45cf-8a37-668793d2ec61)

*Question 2*
---
-- In the Products table, insert a record where some fields are NULL, another record where all fields are filled without any NULL values, and a third record where some fields are filled, and others are left as NULL.

ProductID   Name              Category    Price       Stock
----------  ---------------   ----------  ----------  ----------
106         Fitness Tracker   Wearables
107         Laptop            Electronics  999.99      50
108         Wireless Earbuds  Accessories              100

sql
```
insert into Products(ProductID,Name,Category,Price,Stock)
values(106,'Fitness Tracker','Wearables',null,null),(107,'Laptop','Electronic', 999.99,50),(108,'Wireless Earbud','Accessorie'  ,null,            100)
```

*Output:*

![image](https://github.com/user-attachments/assets/f29a3f65-41c8-4d57-975c-a79a340fa4d2)


*Question 3*
---
-- Create a table named Invoices with the following constraints:

InvoiceID as INTEGER should be the primary key.
InvoiceDate as DATE.
DueDate as DATE should be greater than the InvoiceDate.
Amount as REAL should be greater than 0.

sql
```
create table Invoices(
InvoiceID INTEGER primary key,
InvoiceDate DATE,
DueDate DATE check(DueDate>InvoiceDate),
Amount REAL check (Amount>0)
);
```

*Output:*

![image](https://github.com/user-attachments/assets/a9ef952a-5f7c-447c-8dfb-51b17874d0e0)


*Question 4*
---
-- Write a SQL query to add birth_date attribute as timestamp (datatype) in the table customer 

Sample table: customer

 customer_id |   cust_name    |    city    | grade | salesman_id 
-------------+----------------+------------+-------+-------------
        3002 | Nick Rimando   | New York   |   100 |        5001
        3007 | Brad Davis     | New York   |   200 |        5001
        3005 | Graham Zusi    | California |   200 |        5002

sql
```
ALTER table customer
add column birth_date timestamp;
```

*Output:*

![image](https://github.com/user-attachments/assets/8be38647-ebcd-4c54-bd3c-fec4001dfff4)

*Question 5*
---
--Insert a book with ISBN 978-1234567890, Title Data Science Essentials, Author Jane Doe, Publisher TechBooks, and Year 2024 into the Books table.

For example:

Test	Result
SELECT * FROM Books;
ISBN            Title                    Author      Publisher   Year
--------------  -----------------------  ----------  ----------  ----------
978-1234567890  Data Science Essentials  Jane Doe    TechBooks   2024


sql
```
insert into Books(ISBN ,Title ,Author ,Publisher ,Year)
values('978-1234567890','Data Science Essentials','Jane Doe','TechBooks',2024);
```

*Output:*

![image](https://github.com/user-attachments/assets/b7c8f143-e083-48a9-9f53-beebc2c58e04)


*Question 6*
---
-- Create a new table named contacts with the following specifications:
contact_id as INTEGER and primary key.
first_name as TEXT and not NULL.
last_name as TEXT and not NULL.
email as TEXT.
phone as TEXT and not NULL with a check constraint to ensure the length of phone is at least 10 characters.
For example:

Test	Result
INSERT INTO contacts (contact_id, first_name, last_name, email, phone) VALUES (1, 'John', 'Doe', 'john.doe@example.com', '1234567890');
SELECT * FROM contacts;
contact_id  first_name  last_name   email                 phone
----------  ----------  ----------  --------------------  ----------
1           John        Doe         john.doe@example.com  1234567890


sql
```
create table contacts(
contact_id integer primary key,
first_name TEXT not null,
last_name text not null,
email text,
phone text not null check(length(phone)=10)
);
```

*Output:*

![image](https://github.com/user-attachments/assets/42d76192-df72-4c5d-9f6c-8c60bf1d342a)

*Question 7*
---
-- Create a table named ProjectAssignments with the following constraints:
AssignmentID as INTEGER should be the primary key.
EmployeeID as INTEGER should be a foreign key referencing Employees(EmployeeID).
ProjectID as INTEGER should be a foreign key referencing Projects(ProjectID).
AssignmentDate as DATE should be NOT NULL.

sql
```
create table ProjectAssignments(
AssignmentID integer primary key,
EmployeeID integer,
ProjectID integer,
AssignmentDate Date not null,
foreign key (EmployeeID) references Employees(EmployeeID)
foreign key (ProjectID) references Projects(ProjectID) 
);
```

*Output:*

![image](https://github.com/user-attachments/assets/1124b778-be4b-4eb7-a3c7-66cc38a61383)


*Question 8*
---
-- Create a table named Members with the following columns:

MemberID as INTEGER
MemberName as TEXT
JoinDate as DATE

sql
```
create table Members(
MemberID INTEGER,
MemberName TEXT,
JoinDate DATE
);
```

*Output:*

![image](https://github.com/user-attachments/assets/cebd832a-059d-49a6-9318-b8e875498db8)


*Question 9*
---
-- Create a table named Shipments with the following constraints:
ShipmentID as INTEGER should be the primary key.
ShipmentDate as DATE.
SupplierID as INTEGER should be a foreign key referencing Suppliers(SupplierID).
OrderID as INTEGER should be a foreign key referencing Orders(OrderID)

sql
```
create table Shipments(
ShipmentID integer primary key,
ShipmentDate DATE,
SupplierID integer ,
orderID integer,
foreign key (SupplierID) references Suppliers(SupplierID)
foreign key (OrderID) references Orders(OrderID)
);
```

*Output:*

![image](https://github.com/user-attachments/assets/3c867517-0a7a-4ec5-878f-87c9608b5111)


*Question 10*
---
-- Write a SQL query to modify the Student_details table by adding a new column Email of type VARCHAR(50) and updating the column MARKS to have a default value of 0.

sql
```
CREATE TABLE student_details_new(
    RollNo INTEGER PRIMARY KEY,
    Name TEXT,
    Gender TEXT,
    Subject TEXT,
    MARKS INTEGER DEFAULT 0,
    email VARCHAR(50)
);
INSERT INTO student_details_new (RollNo, Name, Gender, Subject, MARKS)
SELECT RollNo, Name, Gender, Subject, COALESCE(MARKS, 0)
FROM student_details;
ALTER TABLE student_details_new
RENAME TO student_details_new;
```

*Output:*
```
Test	Expected	Got	
INSERT INTO Student_details (RollNo, Name, Gender, Subject, MARKS, Email)
VALUES (104, 'Charlie', 'M', 'History', 88, 'charlie@example.com');
select * from student_details;
RollNo      Name        Gender      Subject     Email                MARKS
----------  ----------  ----------  ----------  -------------------  ----------
104         Charlie     M           History     charlie@example.com  88
RollNo      Name        Gender      Subject     Email                MARKS
----------  ----------  ----------  ----------  -------------------  ----------
104         Charlie     M           History     charlie@example.com  88
```

## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
