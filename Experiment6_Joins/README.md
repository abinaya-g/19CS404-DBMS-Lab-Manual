# Experiment 6: Joins

## AIM
To study and implement different types of joins.

## THEORY

SQL Joins are used to combine records from two or more tables based on a related column.

### 1. INNER JOIN
Returns records with matching values in both tables.

**Syntax:**
```sql
SELECT columns
FROM table1
INNER JOIN table2
ON table1.column = table2.column;
```

### 2. LEFT JOIN
Returns all records from the left table, and matched records from the right.

**Syntax:**

```sql
SELECT columns
FROM table1
LEFT JOIN table2
ON table1.column = table2.column;
```
### 3. RIGHT JOIN
Returns all records from the right table, and matched records from the left.

**Syntax:**

```sql
SELECT columns
FROM table1
RIGHT JOIN table2
ON table1.column = table2.column;
```
### 4. FULL OUTER JOIN
Returns all records when there is a match in either left or right table.

**Syntax:**

```sql
SELECT columns
FROM table1
FULL OUTER JOIN table2
ON table1.column = table2.column;
```

**Question 1**
--
From the following tables write a SQL query to find salespeople who received commissions of more than 12 percent from the company. Return Customer Name, customer city, Salesman, commission.

![image](https://github.com/user-attachments/assets/df1a37c8-edf4-4f44-a547-12467a7d48c2)

Query :
```sql
SELECT c.cust_name as "Customer Name",
c.city AS "city",
s.name AS "Salesman",
s.commission
FROM customer c
JOIN salesman s on c.salesman_id = s.salesman_id
WHERE s.commission > 0.12;

```

**Output:**

![image](https://github.com/user-attachments/assets/e820f85b-c4a8-4ae9-96e6-98afd31eafbe)


**Question 2**
---
Write the SQL query that achieves the selection of all columns from the "test_results" table (aliased as "t"), with an inner join on the "patient_id" column and a condition filtering for patients with the first name 'Alice'.

PATIENTS TABLE:


![image](https://github.com/user-attachments/assets/d3d5a869-ef07-4d7b-a0c4-4be3dfb62d74)

Query :
```sql
SELECT t.*
FROM TEST_RESULTS t
INNER JOIN patients p 
ON t.patient_id = p.patient_id
WHERE p.first_name = 'Alice';
```

**Output:**

![image](https://github.com/user-attachments/assets/2a41a947-109b-4dbe-a00e-fa3d61ddab8b)


**Question 3**
---
From the following tables write a SQL query to locate those salespeople who do not live in the same city where their customers live and have received a commission of more than 12% from the company. Return Customer Name, customer city, Salesman, salesman city, commission.  

![image](https://github.com/user-attachments/assets/f65be8ff-a298-4d00-8656-c1ba331616ec)

Query :
```sql
SELECT 
    c.cust_name AS "Customer Name",
    c.city AS "city",
    s.name AS "Salesman",
    s.city AS "city",
    s.commission
FROM 
    customer c
JOIN 
    salesman s ON c.salesman_id = s.salesman_id
WHERE 
    c.city <> s.city
    AND s.commission > 0.12;

```

**Output:**

![image](https://github.com/user-attachments/assets/b1c41a6e-24c0-4099-942c-bbb5bf9347d5)


**Question 4**
---
Write the SQL query that achieves the selection of all columns from the "patients" table (aliased as "p"), with an inner join on the "patient_id" column and a condition filtering for appointments with an appointment date between '2024-01-01' and '2024-01-31'.

PATIENTS TABLE:

![image](https://github.com/user-attachments/assets/abffd33e-32f3-4cfe-b0dc-5440a71b0c8d)

Query :
```sql
SELECT p.*
FROM patients p
INNER JOIN APPOINTMENTS a
ON p.patient_id = a.patient_id
WHERE a.appointment_date BETWEEN '2024-01-01' AND '2024-01-31';
```

**Output:**

![image](https://github.com/user-attachments/assets/dbb2630f-4928-4253-9593-b50369c0e395)


**Question 5**
---
Write the SQL query that achieves the selection of all columns from the "nurses" table (aliased as "n"), with an inner join on the "department_id" column and a condition filtering for nurses in the 'Pediatrics' department.

NURSES TABLE:

![image](https://github.com/user-attachments/assets/5fa77afe-6490-49a8-8427-9125959dae31)

Query :
```sql
SELECT n.*
FROM nurses n
INNER JOIN DEPARTMENTS d
ON n.department_id = d.department_id
WHERE d.department_name = 'Pediatrics';
```

**Output:**

![image](https://github.com/user-attachments/assets/d7187c40-7bac-4371-b34d-8466b256a274)


**Question 6**
---
Write the SQL query that achieves the selection of all columns from the "customer" table (aliased as "c"), with a left join on the "salesman_id" column and a condition filtering for salesmen with the name 'Mc Lyon'.


![image](https://github.com/user-attachments/assets/25fb0339-4018-4326-aedc-105c7ab3cc01)

Query :
```sql
SELECT c.*
FROM customer c
LEFT JOIN salesman s
ON c.salesman_id = s.salesman_id
WHERE s.name = 'Mc Lyon';
```

**Output:**

![image](https://github.com/user-attachments/assets/01a85a22-a1e7-4a2e-aeb1-f346984c8f0b)


**Question 7**
---
Write a SQL query to find the salesperson and customer who reside in the same city. Return Salesman, cust_name and city.

Sample table: salesman

![image](https://github.com/user-attachments/assets/182b373a-ef0b-4e95-ad6f-8e54f6e3258a)

Query :
```sql
SELECT s.name AS "Salesman",
c.cust_name,s.city
FROM salesman s
JOIN customer c
ON c.city = s.city;
```

**Output:**

![image](https://github.com/user-attachments/assets/7c2f740b-2f6a-4c87-9e44-9ce5166bb6a4)


**Question 8**
---
 From the following tables write a SQL query to find the salesperson(s) and the customer(s) he represents. Return Customer Name, city, Salesman, commission.

Sample table: customer

![image](https://github.com/user-attachments/assets/0458e37b-45d1-4009-a654-939d2dcbb349)

Query :
```sql
SELECT c.cust_name AS "Customer Name",
c.city as "city",
s.name AS "Salesman",
s.commission 
FROM customer c
JOIN salesman s
ON c.salesman_id = s.salesman_id;
```

**Output:**

![image](https://github.com/user-attachments/assets/3f3e1c29-f4a9-491e-bbf7-ac9b2f4802ca)


**Question 9**
---
From the following tables write a SQL query to find the details of an order. Return ord_no, ord_date, purch_amt, Customer Name, grade, Salesman, commission. 

Sample table: orders

![image](https://github.com/user-attachments/assets/581d2b68-c13f-4171-80f6-d77cef1e2896)

![image](https://github.com/user-attachments/assets/c1c0486c-57c0-4eb8-9626-1a7edc2d2992)

Query :
```sql
SELECT o.ord_no,o.ord_date,o.purch_amt,c.cust_name AS "Customer Name",c.grade,s.name as "Salesman",s.commission
FROM orders o
JOIN customer c
ON o.customer_id = c.customer_id
JOIN salesman s
ON o.salesman_id = s.salesman_id;
```

**Output:**

![image](https://github.com/user-attachments/assets/de539907-df72-4777-8cc2-44791996dfe3)


**Question 10**
---
Write the SQL query that achieves the selection of all columns from the "patients" table, with an inner join on the "doctor_id" column, and includes a condition filtering for patients whose doctors have the first name 'John' and last name 'Smith'.

![image](https://github.com/user-attachments/assets/6893b107-0991-42db-9f60-b0148e71a5cd)

Query :
```sql
SELECT p.*
FROM patients p
INNER JOIN doctors d on p.doctor_id = d.doctor_id
WHERE d.first_name = 'John' AND d.last_name = 'Smith';
```

**Output:**

![image](https://github.com/user-attachments/assets/0bc28d7f-bb5c-422e-b30b-180612e86a86)


## RESULT
Thus, the SQL queries to implement different types of joins have been executed successfully.
