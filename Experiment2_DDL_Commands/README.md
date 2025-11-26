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
Create a new table named item with the following specifications and constraints:
    item_id as TEXT and as primary key.
    item_desc as TEXT.
    rate as INTEGER.
    icom_id as TEXT with a length of 4.
    icom_id is a foreign key referencing com_id in the company table.
    The foreign key should set NULL on updates and deletes.
    item_desc and rate should not accept NULL.

```sql
CREATE TABLE item(
    item_id TEXT PRIMARY KEY,
    item_desc TEXT NOT NULL,
    rate INTEGER NOT NULL,
    icom_id TEXT CHECK(LENGTH(icom_id)=4),
    FOREIGN KEY (icom_id) REFERENCES company(com_id)
    ON DELETE SET NULL 
    ON UPDATE SET NULL
);
```

**Output:**

![image](https://github.com/user-attachments/assets/2eebfa33-e414-40c2-9965-f774fbd762ca)



**Question 2**
---
Insert all products from Discontinued_products into Products.
Table attributes are ProductID, ProductName, Price, Stock

```sql
insert into Products(ProductID, ProductName, Price, Stock)
SELECT * FROM Discontinued_products; 
```

**Output:**

![image](https://github.com/user-attachments/assets/7edc5ec7-c274-4173-9d29-be2f37264084)


**Question 3**
---
Create a table named Employees with the following constraints:

EmployeeID should be the primary key.
FirstName and LastName should be NOT NULL.
Email should be unique.
Salary should be greater than 0.
DepartmentID should be a foreign key referencing the Departments table.

```sql
create table Employees(
EmployeeID int primary key,
FirstName text not null,
LastName text not null,
Salary int check(salary>0),
Email text unique,
DepartmentID int,
foreign key (DepartmentID) references Departments(DepartmentID)
);
```

**Output:**

![image](https://github.com/user-attachments/assets/1adf1535-cc33-4e8c-bdb3-c13211382312)


**Question 4**
---
Insert a student with RollNo 201, Name David Lee, Gender M, Subject Physics, and MARKS 92 into the Student_details table
```sql
insert into Student_details(RollNo,Name,Gender,Subject,MARKS)values(201,'David Lee','M','Physics',92)
```

**Output:**

![image](https://github.com/user-attachments/assets/2e6a5949-c3e0-4840-a395-b7f35ba90b10)

**Question 5**
---

Create a table named Members with the following columns:

MemberID as INTEGER
MemberName as TEXT
JoinDate as DATE

```sql
create table Members(
MemberID INTEGER,
MemberName TEXT,
JoinDate DATE);
```

**Output:**

![image](https://github.com/user-attachments/assets/b94e86a9-4b62-4e4a-b1fd-f93cf5b9d677)

**Question 6**
---
Write an SQL query to change the name of the column id to employee_id in the table employee.

```sql
alter table employee  rename id to employee_id; 
```

**Output:**

![image](https://github.com/user-attachments/assets/f03e7c20-39ca-4084-9ce8-a64981818a5b)

**Question 7**
---
Create a table named Attendance with the following constraints:
AttendanceID as INTEGER should be the primary key.
EmployeeID as INTEGER should be a foreign key referencing Employees(EmployeeID).
AttendanceDate as DATE.
Status as TEXT should be one of 'Present', 'Absent', 'Leave'.
```sql
create table Attendance(
    AttendanceID INTEGER PRIMARY KEY,
    EmployeeID INTEGER,
    AttendanceDate DATE,
    Status TEXT ,
    foreign key (EmployeeID) references  Employees(EmployeeID),
    CHECK(Status IN ('Present','Absent','Leave'))
);
```

**Output:**

![image](https://github.com/user-attachments/assets/a78faf98-d2de-4a5b-b892-219f87d96a7f)

**Question 8**
---
Insert the following products into the Products table:

Name        Category     Price       Stock<br/>
----------  -----------  ----------  ----------<br/>
Smartphone  Electronics  800         150<br/>
Headphones  Accessories  200         300<br/>
```sql
insert into Products(Name,Category,Price,Stock)values('Smartphone','Electronics',800,150),('Headphones','Accessories',200,300);
```

**Output:**

![image](https://github.com/user-attachments/assets/be52dd8d-1198-46a3-a0c0-42a01ce48691)

**Question 9**
---

Write a SQL query to add birth_date attribute as timestamp (datatype) in the table customer 

Sample table: customer

 customer_id |   cust_name    |    city    | grade | salesman_id <br/>
-------------+----------------+------------+-------+-------------<br/>
        3002 | Nick Rimando   | New York   |   100 |        5001<br/>
        3007 | Brad Davis     | New York   |   200 |        5001<br/>
        3005 | Graham Zusi    | California |   200 |        5002<br/>

```sql
alter table customer add birth_date timestamp;
```

**Output:**

![image](https://github.com/user-attachments/assets/b17d1491-6ca4-4208-9db7-c4f7390468e3)

**Question 10**
---

Write a SQL query to Add a new column Country as text in the Student_details table.

Sample table: Student_details

 cid              name             type   notnull     dflt_value  pk <br/>
---------------  ---------------  -----  ----------  ----------  ----------<br/>
0                RollNo           int    0                       1<br/>
1                Name             VARCH  1                       0<br/>
2                Gender           TEXT   1                       0<br/>
3                Subject          VARCH  0                       0<br/>
4                MARKS            INT (  0                       0<br/>

```sql

alter table Student_details add Country TEXT;
```

**Output:**

![image](https://github.com/user-attachments/assets/d77662df-626a-4c27-90d9-4f8487ba882e)


## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
