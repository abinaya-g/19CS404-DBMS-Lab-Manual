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
---
Write a SQL statement to Update the per_unit_price to 25 and total_price accordingly in purchases table where purchase_date is '2022-08-15' and product_id is 12.

```sql
UPDATE purchases
SET per_unit_price = 25,
    total_price = 25 * quantity
WHERE purchase_date = '2022-08-15'
  AND product_id = 12;
```

**Output:**

<img width="1533" height="344" alt="image" src="https://github.com/user-attachments/assets/dcd8b08a-d27a-43b6-8672-5ae0afbfb451" />

**Question 2**
---
Write a SQL statement to Increase the selling price per unit by 5% for product ID 15 who's sale is on '2023-01-31'.

sales(sale_id,sale_date,product_id,quantity,sell_price,total_sell_price)

```sql
UPDATE sales
SET sell_price = sell_price * 1.05,
    total_sell_price = sell_price * quantity
WHERE product_id = 15
  AND sale_date = '2023-01-31';
```

**Output:**

<img width="1160" height="287" alt="image" src="https://github.com/user-attachments/assets/6cb30622-d8bd-476f-9094-23c683623dcc" />

**Question 3**
---
Update the reorder level to 40 pieces for all products belonging to the 'Grocery' category in the products table.

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
UPDATE products
SET reorder_lvl = 40
WHERE category = 'Grocery';
```

**Output:**

<img width="1543" height="268" alt="image" src="https://github.com/user-attachments/assets/3c05bec6-078a-4835-8cbb-ff00c58b9b63" />

**Question 4**
---
Write a SQL statement to change the email column of employees table with 'Unavailable' for all employees in employees table.

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
SET email = 'Unavailable';
```

**Output:**

<img width="858" height="309" alt="image" src="https://github.com/user-attachments/assets/96123ad8-a84b-485f-8dae-53486dabf556" />

**Question 5**
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

<img width="1441" height="248" alt="image" src="https://github.com/user-attachments/assets/908e12ef-5d81-4755-9644-2501dd709ae2" />

**Question 6**
---
Write a SQL query to Delete customers from 'customer' table where 'GRADE' is odd.
```sql
DELETE FROM customer
WHERE grade % 2 = 1;
```

**Output:**

<img width="1250" height="204" alt="image" src="https://github.com/user-attachments/assets/47f43d2d-967f-4108-9603-32637e3e2414" />

**Question 7**
---
Write a SQL query to Delete customers from 'customer' table where 'GRADE' is not equal to 3.


```sql
DELETE FROM customer
WHERE grade != 3;
```

**Output:**

<img width="796" height="686" alt="image" src="https://github.com/user-attachments/assets/4f85d3de-314e-498d-99ab-33eb9df836be" />

**Question 8**
---
Write a SQL query to Delete customers from 'customer' table where 'AGENT_CODE' is either 'A003' or 'A008'.


```sql
DELETE FROM customer
WHERE agent_code IN ('A003', 'A008');
```

**Output:**

<img width="918" height="1358" alt="image" src="https://github.com/user-attachments/assets/bf6cc2a4-4913-4879-9681-2732d8f8eb29" />

**Question 9**
---
Write a SQL query to Delete customers with 'GRADE' 2 and 'CUST_NAME' starting with 'M', and whose 'PAYMENT_AMT' is less than 3000


```sql
DELETE FROM customer
WHERE grade = 2
  AND cust_name LIKE 'M%'
  AND payment_amt < 3000;
```

**Output:**

<img width="2020" height="296" alt="image" src="https://github.com/user-attachments/assets/e779e275-d6e8-4e61-ad1f-41bbdd5ea5b4" />

**Question 10**
---
Write a SQL query to Delete customers from 'customer' table where 'GRADE' is exactly 2.


```sql
DELETE FROM customer
WHERE grade = 2;
```

**Output:**

<img width="709" height="647" alt="image" src="https://github.com/user-attachments/assets/16373cb0-5241-4e8f-a85e-6ad3e6e8808b" />


<img width="2415" height="1460" alt="image" src="https://github.com/user-attachments/assets/c784ec31-0434-4b38-94b9-ecbfe0334547" />


## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
