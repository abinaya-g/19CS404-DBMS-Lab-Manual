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
Create a table named Shipments with the following constraints:
* ShipmentID as INTEGER should be the primary key.
* ShipmentDate as DATE.
* SupplierID as INTEGER should be a foreign key referencing Suppliers(SupplierID).
* OrderID as INTEGER should be a foreign key referencing Orders(OrderID).

```sql
create table Shipments(
    ShipmentID INTEGER primary key,
    ShipmentDate DATE,
    SupplierID INTEGER,
    OrderID INTEGER,
    foreign key (SupplierID) references Suppliers(SupplierID),
    foreign key (OrderID) references Orders(OrderID)
);
```

**Output:**

![image](https://github.com/user-attachments/assets/06cbcfdf-5de8-4e02-954f-e3bafde5c5dd)


**Question 2**
---
Create a table named Products with the following constraints:
* ProductID as INTEGER should be the primary key.
* ProductName as TEXT should be unique and not NULL.
* Price as REAL should be greater than 0.
* StockQuantity as INTEGER should be non-negative.

```sql
CREATE TABLE Products(
    ProductID INTEGER primary key,
    ProductName TEXT UNIQUE NOT NULL,
    Price REAL check(price>0),
    StockQuantity INTEGER check(StockQuantity>0)
);
```

**Output:**

![image](https://github.com/user-attachments/assets/dbe82c96-7ea1-4a42-adb5-1d1b64e6b3e8)


**Question 3**
---
Write a SQL query to Rename the "city" column to "location" in the "customer" table.

```sql
alter table customer rename 'city' to 'location';
```

**Output:**

![image](https://github.com/user-attachments/assets/c5b27e17-231d-41ae-a29f-1f6e9378815f)

**Question 4**
---
Write an SQL query to add two new columns, designation and net_salary, to the table Companies. The designation column should have a data type of varchar(50), and the net_salary column should have a data type of number.

```sql
ALTER TABLE Companies add column designation varchar(50);
ALTER TABLE Companies add column net_salary number;
```

**Output:**

![image](https://github.com/user-attachments/assets/664d8036-0144-4915-92f5-4a78d29d8324)

**Question 5**
---
Insert a student with RollNo 201, Name David Lee, Gender M, Subject Physics, and MARKS 92 into the Student_details table.

```sql
INSERT INTO Student_details values(
    201,"David Lee",'M',"Physics",92
);
```

**Output:**

![image](https://github.com/user-attachments/assets/3a29faf3-5cb6-435c-ba56-83df5e3fcaee)


**Question 6**
---
Create a table named Invoices with the following constraints:

* InvoiceID as INTEGER should be the primary key.
* InvoiceDate as DATE.
* DueDate as DATE should be greater than the InvoiceDate.
* Amount as REAL should be greater than 0.

```sql
CREATE TABLE Invoices (
    InvoiceID INTEGER primary key,
    InvoiceDate DATE,
    DueDate Date check (DueDate > InvoiceDate),
    Amount Real check (Amount > 0)
);
```

**Output:**

![image](https://github.com/user-attachments/assets/f88bbefc-2d3b-44d6-baaf-9471a23b6d21)


**Question 7**
---
Create a new table named item with the following specifications and constraints:
* item_id as TEXT and as primary key.
* item_desc as TEXT.
* rate as INTEGER.
* icom_id as TEXT with a length of 4.
* icom_id is a foreign key referencing com_id in the company table.
* The foreign key should cascade updates and deletes.
* item_desc and rate should not accept NULL.

```sql
CREATE TABLE item (
    item_id TEXT Primary key,
    item_desc TEXT NOT NULL,
    rate INTEGER NOT NULL,
    icom_id TEXT check(length(icom_id = 4)),
    foreign key (icom_id) references company(com_id)
    on update cascade
    on delete cascade
);
```

**Output:**

![image](https://github.com/user-attachments/assets/4365dec2-78f4-46e4-bcdd-dbf46ea6bca7)


**Question 8**
---
In the Cusomers table, insert a record where some fields are NULL, another record where all fields are filled without any NULL values, and a third record where some fields are filled, and others are left as NULL.

```sql
INSERT INTO Customers (CustomerID,Name,Address,City,ZipCode) values
    (306,'Diana Prince','Themyscira',NULL,NULL),
    (307,'Bruce Wayne','Wayne Mano',"Gotham",10007),
    (308,'Peter Parker','Queens',NULL,11375)
```

**Output:**

![image](https://github.com/user-attachments/assets/27b7098f-ae9f-4165-882d-69d036ec6dd5)


**Question 9**
---
Create a table named Orders with the following columns:

* OrderID as INTEGER
* OrderDate as TEXT
* CustomerID as INTEGER

```sql
CREATE TABLE Orders (
    OrderID INTEGER,
    OrderDate TEXT,
    CustomerID INTEGER
);
```

**Output:**

![image](https://github.com/user-attachments/assets/95acee90-cf1c-4130-b9b1-a10d15fed13a)


**Question 10**
---
Insert all products from Discontinued_products into Products.

Table attributes are ProductID, ProductName, Price, Stock

```sql
INSERT INTO Products (ProductID, ProductName, Price, Stock) SELECT ProductID, ProductName, Price, Stock FROM Discontinued_products;
```

**Output:**

![image](https://github.com/user-attachments/assets/f5daa2a7-eed8-4521-92ea-9f1ea556465f)



## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.

## Proof
![image](https://github.com/user-attachments/assets/44838c47-29b4-4703-8bc2-c7df3283856a)

