# Experiment 2: DDL Commands
### NAME - AANANDHA KANNAN S

### REG NO - 212224040003

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
Insert all employees from Former_employees into Employee

Table attributes are EmployeeID, Name, Department, Salary

```sql
INSERT INTO employee (EmployeeID, Name, Department,Salary) SELECT EmployeeID, Name, Department, Salary FROM Former_employees;
```

**Output:**

<img width="975" height="199" alt="image" src="https://github.com/user-attachments/assets/d0e48322-1cf0-4aac-a782-448df348443c" />



**Question 2**
---
Create a table named Locations with the following columns:

```sql
create table Locations(
LocationID INTEGER,
LocationName TEXT,
Address TEXT);
```

**Output:**

<img width="1023" height="225" alt="image" src="https://github.com/user-attachments/assets/30dfdc7d-f8f0-4503-84aa-c038e7372647" />


**Question 3**
---
Insert a customer with CustomerID 301, Name Michael Jordan, Address 123 Maple St, City Chicago, and ZipCode 60616 into the Customers table.

```sql
insert into customers(customerId, Name, Address, City, Zipcode)
values(301,'Michael Jordan','123 Maple St','Chicago',60616);
```

**Output:**

<img width="1297" height="118" alt="image" src="https://github.com/user-attachments/assets/76e84220-ce7b-46c7-ab66-a51e1fb9640e" />

**Question 4**
---
Write a SQL query to add birth_date attribute as timestamp (datatype) in the table customer 

```sql
alter table customer
add birth_date timestamp;
```

**Output:**

<img width="769" height="220" alt="image" src="https://github.com/user-attachments/assets/38e9636b-7e04-472b-9cc5-ea475441b76f" />


**Question 5**
---
Create a table named Products with the following constraints:

```sql
create table Products(
ProductID integer primary key,
ProductName text not null unique,
Price real check(price>0),
StockQuantity integer check(stockquantity>=0)
);
```

**Output:**

<img width="450" height="150" alt="image" src="https://github.com/user-attachments/assets/9a555477-e77f-4e58-b03f-241141b4d947" />


**Question 6**
---
Create a table named Department with the following constraints:

```sql
create table Department(
DepartmentID integer primary key,
DepartmentName text not null unique,
Location text);
```

**Output:**

<img width="921" height="156" alt="image" src="https://github.com/user-attachments/assets/096cf4db-a983-4a6d-b423-b18f7c34db13" />


**Question 7**
---
Write an SQL query to change the name of the column id to employee_id in the table employee.

```sql
alter table employee
rename column id to employee_id;
```

**Output:**
<img width="1295" height="208" alt="image" src="https://github.com/user-attachments/assets/28e53f57-2c33-4341-948d-7ea47165942d" />

**Question 8**
---
-- Paste Question 8 hereCreate a new table named products with the following specifications:
```sql
create table products(
product_id integer primary key,
product_name text not null,
list_price decimal(10,2) not null ,
discount decimal(10,2) not null default 0,
check(list_price>=discount),
 check(discount>=0),
 check(list_price>=0)
);
```

**Output:**
<img width="1252" height="234" alt="image" src="https://github.com/user-attachments/assets/2e8a517a-5257-498c-b8f0-18f2eba24dee" />


**Question 9**
---
Create a table named Invoices with the following constraints:



```sql
create table Invoices(
InvoiceID integer primary key,
InvoiceDate date,
DueDate date check(Duedate>Invoicedate),
Amount real check(Amount>0)
);9
```

**Output:**
<img width="1268" height="187" alt="image" src="https://github.com/user-attachments/assets/8f855308-aa5b-46ef-954a-a7f79a85c08f" />


**Question 10**
---
In the Student_details table, insert a student record where some fields are NULL, another record where all fields are filled without any NULL values, and a third record where some fields are filled, and others are left as NULL.

```sql
insert into student_details(RollNo,Name,Gender,Subject,Marks)
values
('205','Olivia Green',"F",NULL,NULL),
('207','Liam Smith','M','Mathematics','85'),
('208','Sophia Johns','F','Science',NULL);
```

**Output:**

<img width="1280" height="206" alt="image" src="https://github.com/user-attachments/assets/cadcaac3-608b-4060-b28d-62c6d7ca6ebe" />


## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
