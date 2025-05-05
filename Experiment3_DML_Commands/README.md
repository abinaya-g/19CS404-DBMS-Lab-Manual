# Experiment 3: DML Commands

## AIM
To study and implement DML (Data Manipulation Language) commands.

## THEORY

### 1. INSERT INTO
Used to add records into a relation.
These are three type of INSERT INTO queries which are as
A)Inserting a single record
**Syntax (Single Row):**
```sql
INSERT INTO table_name (field_1, field_2, ...) VALUES (value_1, value_2, ...);
```
**Syntax (Multiple Rows):**
```sql
INSERT INTO table_name (field_1, field_2, ...) VALUES
(value_1, value_2, ...),
(value_3, value_4, ...);
```
**Syntax (Insert from another table):**
```sql
INSERT INTO table_name SELECT * FROM other_table WHERE condition;
```
### 2. UPDATE
Used to modify records in a relation.
Syntax:
```sql
UPDATE table_name SET column1 = value1, column2 = value2 WHERE condition;
```
### 3. DELETE
Used to delete records from a relation.
**Syntax (All rows):**
```sql
DELETE FROM table_name;
```
**Syntax (Specific condition):**
```sql
DELETE FROM table_name WHERE condition;
```
### 4. SELECT
Used to retrieve records from a table.
**Syntax:**
```sql
SELECT column1, column2 FROM table_name WHERE condition;
```
### Queries:
```
Name: SHYAM S
Reg.NO: 212223240156
```
**Question 1**
--
Update the total selling price to quantity sold multiplied by updated selling price per unit where product id is 10 in the sales table.

SALES TABLE
name               type
-----------------  ---------------
sale_id            INT
sale_date          DATE
product_id         INT
quantity           INT
sell_price         DECIMAL(10,2)
total_sell_price   DECIMAL(10,2)

```sql
update sales
set total_sell_price = quantity * sell_price
where product_id = 10
```

**Output:**

![image](https://github.com/user-attachments/assets/91c0b416-0f63-4ed6-9524-3817d7b08478)

**Question 2**
---
Write a SQL statement to Change the category to 'Household' where product name contains 'Detergent' in the products table.

Products Table 

name          type       
----------    ---------- 
product_id     INT PRIMARY KEY        
product_name   VARCHAR(10) 
category       VARCHAR(50) 
cost_price     DECIMAL(10) 
sell_price     DECIMAL(10) 
reorder_lvl    INT        
quantity       INT        
supplier_id    INT

```sql
update products
set category = 'Household'
where product_name like '%Detergent%';
```

**Output:**

![image](https://github.com/user-attachments/assets/58f8c80b-a8e2-4e10-8d0a-3c95edf23280)

**Question 3**
---
Write a SQL statement to double the availability of the product with product_id 1.

products table

---------------
product_id
product_name
category_id
availability

```sql
update products
set availability = availability * 2
where product_id is 1;
```

**Output:**

![image](https://github.com/user-attachments/assets/57dee195-d6e1-4140-aeb9-bcb50e6ec39b)

**Question 4**
---
Decrease the reorder level by 30 percent where the product name contains 'cream' and quantity in stock is higher than reorder level in the products table.

PRODUCTS TABLE

name               type
-----------------  ---------------
product_id         INT
product_name       VARCHAR(100)
category           VARCHAR(50)
cost_price         DECIMAL(10,2)
sell_price         DECIMAL(10,2)
reorder_lvl        INT
quantity           INT
supplier_id        INT

```sql
update products
set reorder_lvl = reorder_lvl * 0.7
where product_name like '%cream%' and quantity > reorder_lvl;
```

**Output:**

![image](https://github.com/user-attachments/assets/240f611c-172e-4b0d-91ab-191c1fac3920)

**Question 5**
---
Change the supplier name to upper case where contact person contains ' Singh' in suppliers table.

name               type
-----------------  ---------------
supplier_id        INT
supplier_name      VARCHAR(100)
contact_person     VARCHAR(100)
phone_number       VARCHAR(20)
email              VARCHAR(100)
address            VARCHAR(250)

```sql
update suppliers
set supplier_name = UPPER(supplier_name)
where contact_person like '%Singh%'
```

**Output:**

!![image](https://github.com/user-attachments/assets/7ba6650d-3fe9-49d1-bbd9-26e44f01ce8b)

**Question 6**
---
Write a SQL query to Delete all Doctors whose Specialization is either 'Pediatrics' or 'Cardiology' and Last Name is Brown.

Sample table: Doctors

attributes : doctor_id, first_name, last_name, specialization

```sql
delete from doctors
where (specialization = 'Pediatrics' or specialization = 'Cardiology') and last_name = 'Brown';
```

**Output:**

![image](https://github.com/user-attachments/assets/755afd21-8b38-481f-83af-a686c6da85dd)

**Question 7**
---
Write a SQL query to delete a specific doctor from Doctors table whose ID is 1.

Sample table: Doctors

attributes : doctor_id, first_name, last_name, specialization

```sql
delete from doctors
where doctor_id = 1
```

**Output:**

![image](https://github.com/user-attachments/assets/b7f8e00f-d7c4-47c0-9042-2bd1bc9dc09b)

**Question 8**
---
Write a query to fetch details of employees whose EmpLname ends with an alphabet ‘A’ and contains five alphabets.
EmployeeInfo Table

EmpID

EmpFname

EmpLname

Department

Project

Address

DOB

Gender

1

Sanjay

Mehra

HR

P1

Hyderabad(HYD)

01/12/1976

M

2

Ananya

Mishra

Admin

P2

Delhi(DEL)

02/05/1968

F

```sql
select EmpID, EmpFname, EmpLname, Department, Project, Address, DOB, Gender
from EmployeeInfo 
where EmpLname like '%A' and length(EmpLname) = 5;

```

**Output:**

![image](https://github.com/user-attachments/assets/13a1ac1c-a6f7-4966-928b-4183bd5d3d39)

**Question 9**
---
Write a query to list all products that have a discounted price between $100 and $250. Return product_id, original_price, discount_percentage, and discounted_price from products table.

```sql
select product_id, original_price, discount_percentage, original_price * (1 - discount_percentage) as discounted_price from products
where discounted_price between 100 and 250;
```

**Output:**

![image](https://github.com/user-attachments/assets/a17d1481-d6a3-4416-ad26-2237a479f8af)

**Question 10**
---
Write a SQL query to display hire dates in the format "DD-MM-YYYY" from the emp table

cid         name        type        
----------  ----------  ---------- 
0           empno       INT         
1           ename       VARCHAR(100)
2           job         VARCHAR(50)
3           mgr         INT        
4           hiredate    DATE        
5           sal         DECIMAL(10,2)  
6           comm        DECIMAL(10,2)  
7           deptno      INT  

```sql
select ename, substr(hiredate, 9, 2) || '-' || substr(hiredate, 6, 2) || '-' || substr(hiredate, 1, 4) as HireDateFormatted
from emp;
```

**Output:**

![image](https://github.com/user-attachments/assets/a41fd419-ff87-427a-98bc-e876eebe7d07)

## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
