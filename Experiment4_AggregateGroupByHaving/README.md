# Experiment 4: Aggregate Functions, Group By and Having Clause

## AIM
To study and implement aggregate functions, GROUP BY, and HAVING clause with suitable examples.

## THEORY

### Aggregate Functions
These perform calculations on a set of values and return a single value.

- **MIN()** – Smallest value  
- **MAX()** – Largest value  
- **COUNT()** – Number of rows  
- **SUM()** – Total of values  
- **AVG()** – Average of values

**Syntax:**
```sql
SELECT AGG_FUNC(column_name) FROM table_name WHERE condition;
```
### GROUP BY
Groups records with the same values in specified columns.
**Syntax:**
```sql
SELECT column_name, AGG_FUNC(column_name)
FROM table_name
GROUP BY column_name;
```
### HAVING
Filters the grouped records based on aggregate conditions.
**Syntax:**
```sql
SELECT column_name, AGG_FUNC(column_name)
FROM table_name
GROUP BY column_name
HAVING condition;
```
### Queries:
Name: SHYAM S
Reg.NO: 212223240156

**Question 1**
--
What is the total number of appointments scheduled by each doctor?

Sample table:Appointments Table

```sql
SELECT DoctorID, COUNT(*) as TotalAppointments
FROM Appointments
GROUP BY DoctorID;
```

**Output:**

![image](https://github.com/user-attachments/assets/d861763b-715e-4fee-8d04-0fa66749ded4)

**Question 2**
---
How many patients are covered by each insurance company?

Sample table:Insurance Table

name               type
-----------------  ----------
InsuranceID        INTEGER
PatientID          INTEGER
InsuranceCompany   TEXT
PolicyNumber       TEXT
PolicyHolder       TEXT
ValidityPeriod     TEXT

```sql
SELECT insuranceCompany, COUNT(DISTINCT PatientID) as TotalPatients 
FROM Insurance
GROUP BY InsuranceCompany;
```

**Output:**

![image](https://github.com/user-attachments/assets/31975413-295e-413c-b5dc-5609078451a2)

**Question 3**
---
How many doctors specialize in each medical specialty?

Sample table:Doctors Table

```sql
SELECT Specialty, COUNT(*) as TotalDocto
FROM Doctors
GROUP BY Specialty;
```

**Output:**

![image](https://github.com/user-attachments/assets/2570feea-e149-436a-bd7b-4ec023f34715)

**Question 4**
---
Write a SQL query to Calculate the average email length (in characters) for people who lives in Mumbai city

Table: customer

name        type
----------  ----------
id          INTEGER
name        TEXT   
city        TEXT
email       TEXT
phone       INTEGER

```sql
SELECT AVG(LENGTH(email)) AS avg_email_length_below_30
FROM customer
WHERE city='Mumbai';
```

**Output:**

![image](https://github.com/user-attachments/assets/72450d0d-92d0-4b86-b3da-cfc3c3834a94)

**Question 5**
---
Write a SQL query to find What is the age difference between the youngest and oldest employee in the company.

Table: employee

name        type
----------  ----------
id          INTEGER
name        TEXT
age         INTEGER
city        TEXT
income      INTEGER

```sql
SELECT MAX(age)-MIN(age) as age_difference
FROM employee;
```

**Output:**

![image](https://github.com/user-attachments/assets/54e65c0f-8a1c-4195-9d44-b298c2d9f2fc)

**Question 6**
---
Write a SQL query that counts the number of unique salespeople. Return number of salespeople.

Sample table: orders

ord_no      purch_amt   ord_date    customer_id  salesman_id

----------  ----------  ----------  -----------  -----------

70001       150.5       2012-10-05  3005         5002

70009       270.65      2012-09-10  3001         5005

70002       65.26       2012-10-05  3002         5001

```sql
SELECT COUNT(DISTINCT salesman_id) as COUNT
FROM orders;
```

**Output:**

![image](https://github.com/user-attachments/assets/faf186e9-ad66-4984-b943-90a2a835a832)

**Question 7**
---
Write a SQL query to find the average length of email addresses (in characters):

Table: customer

name        type
----------  ----------
id          INTEGER
name        TEXT
city        TEXT
email       TEXT
phone       INTEGER

```sql
SELECT AVG(LENGTH(email)) as avg_email_length
FROM customer;
```

**Output:**

![image](https://github.com/user-attachments/assets/165baf6f-4853-47db-9981-0daf7eab6bab)

**Question 8**
---
Write the SQL query that accomplishes the selection of number of products for each category from products table which includes only those products where the category ID is greater than 2.

Sample table: products

```sql
SELECT category_id, COUNT(*) as COUNT
FROM products
WHERE category_id > 2
GROUP BY category_id;
```

**Output:**

![image](https://github.com/user-attachments/assets/af8ee33c-f3e6-46a3-93f2-db40f5bff5b2)

**Question 9**
---
Write the SQL query that achieves the grouping of data by age, calculates the minimum income for each age group, and includes only those age groups where the minimum income is less than 1,000,000.

Sample table: employee

```sql
SELECT age, MIN(income) as Income
FROM employee
GROUP BY age
HAVING MIN(income) < 1000000;
```

**Output:**

![image](https://github.com/user-attachments/assets/3ad09c85-2e0a-45e8-b8cc-490333eb4740)

**Question 10**
---
Write the SQL query that accomplishes the selection of average price for each category from the "products" table and includes only those products where the average price falls between 10 and 15.

Sample table: products

```sql
SELECT category_id, AVG(price) as "AVG(Price)"
FROM products
GROUP BY category_id
HAVING AVG(price) BETWEEN 10 and 15;
```

**Output:**

![image](https://github.com/user-attachments/assets/9f53f017-4e09-471c-ad6c-e91d00d73c22)

## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
