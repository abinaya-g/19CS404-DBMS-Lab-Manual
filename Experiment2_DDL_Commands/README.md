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
```
Create a table named Reviews with the following columns:
  ReviewID as INTEGER
  ProductID as INTEGER
  Rating as REAL
  ReviewText as TEXT
```

**Output:**

<img width="1237" height="771" alt="image" src="https://github.com/user-attachments/assets/246b369f-8684-4270-823d-9ad8f5e147bc" />


**Question 2**

```sql
Create a new table named item with the following specifications and constraints:
  item_id as TEXT and as primary key.
  item_desc as TEXT.
  rate as INTEGER.
  icom_id as TEXT with a length of 4.
  icom_id is a foreign key referencing com_id in the company table.
  The foreign key should cascade updates and deletes.
  item_desc and rate should not accept NULL.
```

**Output:**

<img width="1246" height="722" alt="image" src="https://github.com/user-attachments/assets/63286e3c-6a63-43d7-b899-0db24af40edb" />


**Question 3**

```sql
Create a table named Department with the following constraints:
  DepartmentID as INTEGER should be the primary key.
  DepartmentName as TEXT should be unique and not NULL.
  Location as TEXT.
```

**Output:**

<img width="1242" height="676" alt="image" src="https://github.com/user-attachments/assets/324b5c5c-5cf2-4ffc-bba5-e5f82dcc7e85" />


**Question 4**

```sql
Insert a new product with ProductID 101, Name Laptop, Category Electronics, Price 1500, and Stock 50 into the Products table.
```

**Output:**

<img width="1246" height="640" alt="image" src="https://github.com/user-attachments/assets/5cff9315-a6e9-472c-ae41-5d7f43d03e36" />


**Question 5**

```sql
Create a new table named contacts with the following specifications:
  contact_id as INTEGER and primary key.
  first_name as TEXT and not NULL.
  last_name as TEXT and not NULL.
  email as TEXT.
  phone as TEXT and not NULL with a check constraint to ensure the length of phone is at least 10 characters.
```

**Output:**

<img width="1247" height="762" alt="image" src="https://github.com/user-attachments/assets/6eb3f469-ff29-4b7e-a6a6-09ee52802504" />


**Question 6**

```sql
Insert the following products into the Products table:

Name        Category     Price       Stock
----------  -----------  ----------  ----------
Smartphone  Electronics  800         150
Headphones  Accessories  200         300
```

**Output:**
<img width="1220" height="713" alt="image" src="https://github.com/user-attachments/assets/f340a1ba-2f26-403f-a7d8-e5e6e8a6f7d3" />

**Question 7**

```sql
Write an SQL Query to add the attributes designation, net_salary, and dob to the Companies table with the following data types:
  designation as VARCHAR(50)
  net_salary as NUMBER
  dob as DATE
```

**Output:**
<img width="1247" height="772" alt="image" src="https://github.com/user-attachments/assets/b4052a87-46da-4ec6-b242-595785e52151" />


**Question 8**

```sql
Insert all books from Out_of_print_books into Books
Table attributes are ISBN, Title, Author, Publisher, YearPublished
```

**Output:**

<img width="1238" height="692" alt="image" src="https://github.com/user-attachments/assets/90451dcb-aba6-40f8-a67f-072f610f30e1" />


**Question 9**

```sql
Write an SQL query to add a new column email of type TEXT to the Student_details table, and ensure that this column cannot contain NULL values and make default value as 'Invalid'
```

**Output:**

<img width="1227" height="641" alt="image" src="https://github.com/user-attachments/assets/5c90f887-bb7c-4689-b143-07d820b42b7e" />


**Question 10**

```sql
Create a table named ProjectAssignments with the following constraints:
  AssignmentID as INTEGER should be the primary key.
  EmployeeID as INTEGER should be a foreign key referencing Employees(EmployeeID).
  ProjectID as INTEGER should be a foreign key referencing Projects(ProjectID).
  AssignmentDate as DATE should be NOT NULL.
```

**Output:**

<img width="1250" height="686" alt="image" src="https://github.com/user-attachments/assets/3db44124-bc49-4192-8e68-cc128b014820" />



## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
