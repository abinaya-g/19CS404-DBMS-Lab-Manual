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
Insert all employees from Former_employees into Employee

Table attributes are EmployeeID, Name, Department, Salary

SQL CODE :
````
insert into Employee(EmployeeID,Name,Department,Salary)
SELECT EmployeeID,Name,Department,Salary
FROM Former_employees
````

**Output:**

![image](https://github.com/user-attachments/assets/29ca0b4f-2ac1-4a02-a2f6-147386cfc235)

**Question 2**
---
Write an SQL query to add a new column salary of type INTEGER to the Employees table, with a CHECK constraint that ensures the value in this column is greater than 0.

SQL CODE :
```
alter table Employees add column salary INTEGER;
```

**Output:**
---
![image](https://github.com/user-attachments/assets/9f77459a-3bc2-4723-b878-9f4bc0366cbf)

**Question 3**
---
Create a new table named contacts with the following specifications:
contact_id as INTEGER and primary key.
first_name as TEXT and not NULL.
last_name as TEXT and not NULL.
email as TEXT.
phone as TEXT and not NULL with a check constraint to ensure the length of phone is at least 10 characters

SQL CODE :
```
CREATE TABLE contacts(
contact_id INTEGER PRIMARY KEY,
first_name TEXT NOT NULL,
last_name TEXT NOT NULL,
email TEXT,
phone TEXT NOT NULL
check(
length(phone)>=10));
```

**Output:**

![image](https://github.com/user-attachments/assets/183321fd-130e-4216-b11f-8aec4086b80c)

**Question 4**
---
Insert the below data into the Student_details table, allowing the Subject and MARKS columns to take their default values.

RollNo      Name          Gender      
----------  ------------  ----------  
204         Samuel Black  M          

Note: The Subject and MARKS columns will use their default values.

SQL CODE :
```
INSERT INTO Student_details(Rollno,Name,Gender)
values(204,'Samuel Black','M');
```

**Output:**

![image](https://github.com/user-attachments/assets/db11b299-24ed-44df-b73e-3c23f0cac3d6)


**Question 5**
---
Create a table named Products with the following constraints:

ProductID should be the primary key.
ProductName should be NOT NULL.
Price is of real datatype and should be greater than 0.
Stock is of integer datatype and should be greater than or equal to 0.

SQL CODE :
```
CREATE TABLE Products(
ProductID PRIMARY KEY,
ProductName NOT NULL,
Price FLOAT,
Stock INTEGER
check(
Price>=0 and
Stock>=0));
```

**Output:**

![image](https://github.com/user-attachments/assets/3154a922-96b4-4882-9bbb-0c496ab35f9d)


**Question 6**
---
Create a table named Employees with the following constraints:

EmployeeID should be the primary key.
FirstName and LastName should be NOT NULL.
Email should be unique.
Salary should be greater than 0.
DepartmentID should be a foreign key referencing the Departments table.

SQL CODE :
```
CREATE TABLE Employees(
EmployeeID INT PRIMARY KEY,
FirstName VARCHAR(50) NOT NULL,
LastName VARCHAR(50) NOT NULL,
Email unique,
Salary INT check(Salary>0),
DepartmentID INT,
FOREIGN KEY(DepartmentID) references Departments(DepartmentID));
```

**Output:**

![image](https://github.com/user-attachments/assets/12c4ab15-2a29-4caf-8292-c69a11e3235b)

**Question 7**
---
Create a new table named item with the following specifications and constraints:
item_id as TEXT and as primary key.
item_desc as TEXT.
rate as INTEGER.
icom_id as TEXT with a length of 4.
icom_id is a foreign key referencing com_id in the company table.
The foreign key should cascade updates and deletes.
item_desc and rate should not accept NULL.

SQL CODE :
```
CREATE TABLE item (
    item_id TEXT PRIMARY KEY,
    item_desc TEXT NOT NULL,
    rate INTEGER NOT NULL,
    icom_id TEXT CHECK (LENGTH(icom_id) = 4),
    FOREIGN KEY (icom_id) REFERENCES company(com_id) 
    ON UPDATE CASCADE 
    ON DELETE CASCADE
);
```

**Output:**

![image](https://github.com/user-attachments/assets/c9a72282-09fb-433f-ad5a-a9e01d3fec34)


**Question 8**
---
Write a SQL query to Add a new column mobilenumber as number in the Student_details table.

Sample table: Student_details

 cid              name             type   notnull     dflt_value  pk
---------------  ---------------  -----  ----------  ----------  ----------
0                RollNo           int    0                       1
1                Name             VARCH  1                       0
2                Gender           TEXT   1                       0
3                Subject          VARCH  0                       0
4                MARKS            INT (  0                       0

SQL CODE :
```
ALTER TABLE Student_details 
ADD COLUMN mobilenumber number;
```

**Output:**

![image](https://github.com/user-attachments/assets/ddb645e0-5cdf-4f00-8f99-956fef209f83)

**Question 9**
---
Create a table named Reviews with the following columns:

ReviewID as INTEGER
ProductID as INTEGER
Rating as REAL
ReviewText as TEXT

SQL CODE :

```
CREATE TABLE Reviews(
ReviewID INTEGER,
ProductID INTEGER,
Rating REAL,
ReviewText TEXT);
```

**Output:**

![image](https://github.com/user-attachments/assets/06d009a6-6b2d-4fb9-a310-a11f75bddcc0)

**Question 10**
---
Insert the following customers into the Customers table:

CustomerID  Name         Address     City        ZipCode
----------  -----------  ----------  ----------  ----------
302         Laura Croft  456 Elm St  Seattle     98101
303         Bruce Wayne  789 Oak St  Gotham      10001

SQL CODE :
```sql

INSERT INTO Customers(CustomerID,Name,Address,City,ZipCode)
values(302,'Laura Croft','456 Elm St','Seattle',98101),(303,'Bruce Wayne','789 Oak St','Gotham','10001');
```

**Output:**

![image](https://github.com/user-attachments/assets/0acc5f6f-e77b-4731-93dd-8313018a0745)


## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
