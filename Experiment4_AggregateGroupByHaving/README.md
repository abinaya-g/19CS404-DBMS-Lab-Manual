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

**Question 1**
--



```sql
SELECT MAX(price) - MIN(price) AS price_diff
FROM fruits;
```

**Output:**




**Question 2**
---




```sql
SELECT COUNT(*) AS employees_count
FROM employee
WHERE income > 50000;
```

**Output:**


**Question 3**
---


<img width="981" height="482" alt="image" src="https://github.com/user-attachments/assets/aa44259a-9e3c-472a-921a-8be3a7021209" />



```sql
SELECT SUM(purch_amt) AS TOTAL
FROM orders;
```

**Output:**


<img width="502" height="409" alt="image" src="https://github.com/user-attachments/assets/b3cde9b4-41f2-4167-b1ed-31fbc90c8d06" />


**Question 4**
---

<img width="729" height="650" alt="image" src="https://github.com/user-attachments/assets/995e294c-7717-4edc-9de6-f99d2ee7926b" />


```sql
SELECT 
    strftime('%H', AppointmentDateTime) AS HourOfDay,
    COUNT(*) AS TotalAppointments
FROM Appointments
GROUP BY strftime('%H', AppointmentDateTime)
ORDER BY HourOfDay;
```

**Output:**


<img width="784" height="552" alt="image" src="https://github.com/user-attachments/assets/3ab54c88-3799-46c3-9513-438290fda808" />

**Question 5**
---

<img width="1011" height="509" alt="image" src="https://github.com/user-attachments/assets/4968f7d7-e175-4ae2-9841-352c9bcd2791" />


```sql
SELECT 
    Address,
    COUNT(*) AS TotalPatients
FROM Patients
GROUP BY Address;
```

**Output:**

<img width="765" height="497" alt="image" src="https://github.com/user-attachments/assets/4f6b08d0-b4e0-4c86-8261-b397ac70a191" />

**Question 6**
---

<img width="1090" height="594" alt="image" src="https://github.com/user-attachments/assets/d49561b1-af27-40c6-b583-f5cf2df12d83" />


```sql
SELECT 
    Frequency,
    COUNT(*) AS TotalPrescriptions
FROM Prescriptions
GROUP BY Frequency;
```

**Output:**


<img width="847" height="546" alt="image" src="https://github.com/user-attachments/assets/5468d022-c050-4ed5-9ba3-35b83d1d93ec" />


**Question 7**
---

<img width="1223" height="475" alt="image" src="https://github.com/user-attachments/assets/053a1b4a-5939-4feb-a20a-b7cb8d548090" />


```sql
SELECT 
    address,
    AVG(salary) AS "AVG(salary)"
FROM customer1
GROUP BY address
HAVING AVG(salary) > 5000;
```

**Output:**

<img width="667" height="454" alt="image" src="https://github.com/user-attachments/assets/5873f232-b92e-4f35-8e63-4afc78e66c21" />


**Question 8**
---

<img width="1244" height="451" alt="image" src="https://github.com/user-attachments/assets/65db6982-cd97-415f-9672-9802b7a9b2e2" />


```sql
SELECT 
    age AS age_group,
    MIN(salary) AS "MIN(salary)"
FROM customer1
GROUP BY age
HAVING MIN(salary) < 2000
   AND age = 25;
```

**Output:**


<img width="678" height="414" alt="image" src="https://github.com/user-attachments/assets/a243973d-6b05-4a4c-9bb1-774b6b9c81ce" />


**Question 9**
---

<img width="1208" height="476" alt="image" src="https://github.com/user-attachments/assets/0e88891e-b8d2-48ea-8d90-81ee308d9132" />


```sql
SELECT 
    jdate,
    MAX(workhour) AS "MAX(workhour)"
FROM employee1
GROUP BY jdate
HAVING MAX(workhour) > 12;
```

**Output:**


<img width="678" height="414" alt="image" src="https://github.com/user-attachments/assets/0f8624be-4944-4aed-8120-0d276d622d70" />


**Question 10**
---

<img width="1227" height="541" alt="image" src="https://github.com/user-attachments/assets/db104a11-0cec-4373-b846-aa541b60b88d" />


```sql
SELECT 
    category_id,
    COUNT(product_name) AS "count(product_name)"
FROM products
GROUP BY category_id
HAVING category_id < 3;
```

**Output:**

<img width="880" height="403" alt="image" src="https://github.com/user-attachments/assets/0152520e-7db7-4c3a-87e0-f68acaa2fffa" />


## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
