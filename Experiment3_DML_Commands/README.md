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
Write a SQL query to reduce the reorder level by 30% where cost price is more than 50 and quantity in stock is less than 100 in the products table.

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
UPDATE products
SET reorder_lvl = reorder_lvl * 0.7
WHERE cost_price > 50
  AND quantity < 100;
```

**Output:**

<img width="1227" height="525" alt="image" src="https://github.com/user-attachments/assets/b581881d-cc43-4b9e-87d0-c0e54dba1efa" />


**Question 2**
---
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
UPDATE sales
SET total_sell_price = quantity * sell_price
WHERE product_id = 10;
```

**Output:**

<img width="1227" height="577" alt="image" src="https://github.com/user-attachments/assets/45ba683b-c21b-45ff-934d-aa721d06c51e" />


**Question 3**
---
Write a SQL statement to change the first_name column of employees table with 'John' for those employees whose department_id is 80 and gets a commission_pct below 0.35.

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

```sql
UPDATE employees
SET first_name = 'John'
WHERE department_id = 80
  AND commission_pct < 0.35;

```

**Output:**

<img width="1227" height="627" alt="image" src="https://github.com/user-attachments/assets/dc71182b-6da9-4e03-bd51-518d44592b0b" />


**Question 4**
---
Write a SQL query to Delete customers from 'customer' table where 'GRADE' is greater than or equal to 2.


```sql
DELETE FROM customer
WHERE GRADE >= 2;
```

**Output:**

<img width="1226" height="620" alt="image" src="https://github.com/user-attachments/assets/42f47e48-00e0-4726-980a-b89ae8391094" />


**Question 5**
---
Write a SQL query to Delete a Specific Surgery whose ID is 3

Sample table: Surgeries

attributes: surgery_id, patient_id, surgeon_id, surgery_date
For example:

Test	Result
SELECT * FROM surgeries;
surgery_id  patient_id  surgeon_id  surgery_date
----------  ----------  ----------  ------------
1           1           1           2024-01-15
2           2           2           2024-02-28
3           3           3           2024-03-25
surgery_id  patient_id  surgeon_id  surgery_date
----------  ----------  ----------  ------------
1           1           1           2024-01-15
2           2           2           2024-02-28

```sql
DELETE FROM surgeries
WHERE surgery_id = 3;
```

**Output:**

<img width="1223" height="461" alt="image" src="https://github.com/user-attachments/assets/6b5ce9a1-d95a-4633-93a3-d1651daf7697" />


**Question 6**
---
Write a SQL query to delete a specific doctor from Doctors table whose ID is 1.

Sample table: Doctors

attributes : doctor_id, first_name, last_name, specialization

```sql
DELETE FROM doctors
WHERE doctor_id = 1;
```

**Output:**

<img width="1225" height="335" alt="image" src="https://github.com/user-attachments/assets/ff5d55b3-fee3-4f70-9808-76542aaaff69" />


**Question 7**
---
Write a SQL statement to retrieve city(column name) of all customers from customers table without any repeats.

```sql
SELECT DISTINCT city
FROM customers;
```

**Output:**

<img width="1223" height="606" alt="image" src="https://github.com/user-attachments/assets/e3665595-4737-4ef3-b9ed-415743d310fe" />


**Question 8**
---
Write a SQL query to assign a priority of 'Low', 'Medium', or 'High' to value2 based on whether it is less than 20, between 20 and 50, or greater than 50, respectively in the Calculations table.

cid         name        type        notnull     dflt_value  pk
----------  ----------  ----------  ----------  ----------  ----------
0           id          INTEGER     0                       1
1           value1      REAL        0                       0
2           value2      REAL        0                       0
3           base        INTEGER     0                       0
4           exponent    INTEGER     0                       0
5           number      REAL        0                       0
6           decimal     REAL        0                       0
 

```sql
SELECT 
    id,
    value2,
    CASE
        WHEN value2 < 20 THEN 'Low'
        WHEN value2 >= 20 AND value2 <= 50 THEN 'Medium'
        WHEN value2 > 50 THEN 'High'
    END AS priority
FROM Calculations;
```

**Output:**

<img width="1228" height="549" alt="image" src="https://github.com/user-attachments/assets/73cb77ff-1659-4af1-aad2-22ff0358cea1" />


**Question 9**
---
Write a SQL query to find customers who are either from the city 'New York' or who have a grade greater than 200. Return customer_id, cust_name, city, grade, and salesman_id.

```sql
SELECT customer_id, cust_name, city, grade, salesman_id
FROM customer
WHERE city = 'New York'
   OR grade > 200;
```

**Output:**

<img width="1223" height="520" alt="image" src="https://github.com/user-attachments/assets/4f0c9a67-cafe-4291-99cc-1fbef5100efc" />


**Question 10**
---
Write a SQL query to calculate the discounted price for products whose original price is between $50 and $150. Return product_id, original_price, discount_percentage, and discounted_price.

Sample table: Products

product_id | original_price | discount_percentage

 ------------+----------------+--------------------- 

101 | 50.00 | 0.10 

102 | 125.00 | 0.15

 103 | 200.00 | 0.20

```sql
SELECT 
    product_id,
    original_price,
    discount_percentage,
    original_price * (1 - discount_percentage) AS discounted_price
FROM Products
WHERE original_price BETWEEN 50 AND 150;
```

**Output:**

<img width="1225" height="365" alt="image" src="https://github.com/user-attachments/assets/8ec1acaf-7b44-404c-b8af-bde211ffc8b0" />
## GRADE## 
<img width="770" height="606" alt="image" src="https://github.com/user-attachments/assets/7e6d1e23-9503-41fb-8c77-1586f2401d57" />




## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
