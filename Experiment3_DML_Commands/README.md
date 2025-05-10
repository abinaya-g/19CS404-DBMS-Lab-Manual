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
**Question 1**
--
Write a SQL statement to Update the reorder level to 20 where the quantity in stock is less than 10 and product category is 'Snacks' in the products table.

Products table

---------------
product_id
product_name
category
cost_price
sell_price
reorder_lvl
quantity
supplier_id

![image](https://github.com/user-attachments/assets/0bf8308a-c79f-48f3-932e-f0f82fc8286b)

Query :
```sql
UPDATE Products
SET reorder_lvl=20
WHERE quantity < 10 AND category = 'Snacks';
```

**Output:**

![image](https://github.com/user-attachments/assets/d8423817-1c0d-49df-ad77-28fcf2a12d01)


**Question 2**
---
For  Increase the selling price per unit by 3 for all products supplied by supplier ID 4 in the sales table.

PRODUCTS TABLE

![image](https://github.com/user-attachments/assets/2fe7b3e1-e9d0-40d9-8f46-c3dfa10f97ca)

Query :
```sql
UPDATE SALES
SET sell_price = sell_price + 3
WHERE product_id IN (
SELECT product_id FROM PRODUCTS
WHERE supplier_id =4);
```

**Output:**

![image](https://github.com/user-attachments/assets/f8c5dff2-27eb-4639-9621-0184e2195f9e)

**Question 3**
---
Write a SQL statement to Double the salary for employees in department 20 who have a job_id ending with 'MAN'

Employees table
---------------
employee_id
first_name
last_name
email
phone_number
hire_date
job_id
salary
commission_pct
manager_id
department_id

![image](https://github.com/user-attachments/assets/a7d20c64-ae92-48b3-bc23-7464793f608c)

Query :
```sql
UPDATE Employees
SET salary = salary * 2
WHERE job_id LIKE '%MAN%';
```

**Output:**

![image](https://github.com/user-attachments/assets/e8c5b1b2-f43a-42b8-aef5-91666e35323f)

**Question 4**
---
Write a SQL statement to Update the per_unit_price to 25 and total_price accordingly in purchases table where purchase_date is '2022-08-15' and product_id is 12.

![image](https://github.com/user-attachments/assets/3a959661-f740-4a53-a2e5-c719abf7fb27)

Query :
```sql
UPDATE purchases
SET per_unit_price = 25,
total_price = quantity * 25
WHERE purchase_date = '2022-08-15' AND product_id = 12;
```

**Output:**

![image](https://github.com/user-attachments/assets/a3388ff0-fdd0-4278-bd53-94da511ad18e)

**Question 5**
---
Change the supplier name to upper case where contact person contains ' Singh' in suppliers table.

![image](https://github.com/user-attachments/assets/b36053ca-30ac-4177-801a-99731fdb852a)

Query :
```sql
UPDATE suppliers
SET supplier_name = UPPER(supplier_name)
WHERE contact_person LIKE '%Singh%';
```

**Output:**

![image](https://github.com/user-attachments/assets/5ea86826-e39d-42c0-8311-7e20a49a5da4)

**Question 6**
---
Write a SQL query to Delete All Doctors with a NULL Specialization

Sample table: Doctors

attributes : doctor_id, first_name, last_name, specialization

![image](https://github.com/user-attachments/assets/453b33c7-aa7c-447c-96d1-17fece1f0be1)

Query :
```sql
DELETE FROM Doctors
WHERE specialization IS NULL;
```

**Output:**

![image](https://github.com/user-attachments/assets/ef281edd-9520-47ab-a8e8-56949bd0ac3c)

**Question 7**
---
Write a SQL query to Delete customers from 'customer' table where 'CUST_NAME' has exactly 6 characters

![image](https://github.com/user-attachments/assets/86cdc930-4320-4dba-9e9b-cb900063e6b1)

Query :
```sql
DELETE FROM Customer
WHERE LENGTH(CUST_NAME)=6;
```

**Output:**

![image](https://github.com/user-attachments/assets/48df7040-5928-4073-83ae-ecb07b30e3c9)

**Question 8**
---
Write a query to find the names of employees that begin with ‘S’ from EmployeeInfo table.

![image](https://github.com/user-attachments/assets/026653a2-a828-4318-80c8-678b35f06748)

Query :
```sql
SELECT * FROM EmployeeInfo
WHERE EmpFname LIKE '%S%';
```

**Output:**

![image](https://github.com/user-attachments/assets/9e58e5b6-6bc6-4d4a-8ff9-cb2c8b087a42)

**Question 9**
---
Write a SQL query to assign a priority of 'Low', 'Medium', or 'High' to value2 based on whether it is less than 20, between 20 and 50, or greater than 50, respectively in the Calculations table.

![image](https://github.com/user-attachments/assets/28318dd8-82dc-4c25-8cb8-4a8ca534d5af)

Query :
```sql
SELECT id,value2,
CASE
WHEN value2<20 THEN 'Low'
WHEN value2 BETWEEN 20 AND 50 THEN 'Medium'
ELSE 'High'
END AS priority
FROM Calculations;
```

**Output:**


![image](https://github.com/user-attachments/assets/4fbd8624-e1c2-401c-b144-cb6d61741c9b)

**Question 10**
---
write a SQL query to find details of all orders with a purchase amount less than 200 or exclude orders with an order date greater than or equal to '2012-02-10' and a customer ID less than 3009. Return ord_no, purch_amt, ord_date, customer_id and salesman_id.

Sample table: orders

![image](https://github.com/user-attachments/assets/51c9c36a-6d47-4204-87a9-94a867bf7b45)

Query :
```sql
SELECT ord_no,purch_amt,ord_date,customer_id,salesman_id FROM orders
WHERE purch_amt < 200 OR (ord_date <'2012-02-10' AND customer_id <3009) OR customer_id = 3009;
```

**Output:**

![image](https://github.com/user-attachments/assets/98a62a3f-1de2-480d-9045-547295115cb4)

## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
