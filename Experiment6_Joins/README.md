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
![Screenshot 2025-04-29 174951](https://github.com/user-attachments/assets/51de584c-3ddc-4a0d-b694-8594524fff59)

```sql
SELECT 
    p.first_name AS patient_name,
    d.specialization AS Doctor_specialization
FROM 
    patients p
INNER JOIN 
    doctors d ON p.doctor_id = d.doctor_id
WHERE 
    p.admission_date BETWEEN '2024-01-01' AND '2024-01-31';
```

**Output:**

![Screenshot 2025-04-29 175028](https://github.com/user-attachments/assets/d9cf39f6-5a13-4d07-8cf1-d424396acddf)


**Question 2**
---
![Screenshot 2025-04-29 175043](https://github.com/user-attachments/assets/486d526a-ea02-4f3e-80e1-ad3401b5d8ea)


```sql
SELECT 
    c.cust_name, 
    c.city, 
    c.grade, 
    s.name AS Salesman, 
    s.city AS city
FROM 
    customer c
INNER JOIN 
    salesman s ON c.salesman_id = s.salesman_id
ORDER BY 
    c.customer_id ASC;
```

**Output:**

![Screenshot 2025-04-29 175058](https://github.com/user-attachments/assets/135766cc-70d0-4c65-b6ce-07a2673a7862)


**Question 3**
---
![Screenshot 2025-04-29 175118](https://github.com/user-attachments/assets/e2a08b21-ea87-49c3-9acd-c79161b09f96)


```sql
SELECT 
    c.cust_name,
    c.city,
    o.ord_no,
    o.ord_date,
    o.purch_amt AS "Order Amount",
    s.name,
    s.commission
FROM 
    customer c
LEFT JOIN 
    orders o ON c.customer_id = o.customer_id
LEFT JOIN 
    salesman s ON o.salesman_id = s.salesman_id
ORDER BY 
    c.cust_name, o.ord_date;


```

**Output:**

![Screenshot 2025-04-29 175139](https://github.com/user-attachments/assets/f209b528-a264-4fe2-b428-672c70d4bf17)


**Question 4**
---
![Screenshot 2025-04-29 175152](https://github.com/user-attachments/assets/d442c479-b047-4f7b-a687-cb15620e5971)


```sql
SELECT 
    o.ord_no,
    o.ord_date,
    o.purch_amt,
    c.cust_name AS "Customer Name",
    c.grade,
    s.name AS "Salesman",
    s.commission
FROM 
    orders o
JOIN 
    customer c ON o.customer_id = c.customer_id
JOIN 
    salesman s ON o.salesman_id = s.salesman_id
ORDER BY 
    o.ord_no;

```

**Output:**

![Screenshot 2025-04-29 175205](https://github.com/user-attachments/assets/0d26964f-dec2-4f2b-9755-a0b7c9b97d82)


**Question 5**
---
![Screenshot 2025-04-29 175217](https://github.com/user-attachments/assets/2507adf1-d65c-4666-b374-f5c7d2452e88)


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
![Screenshot 2025-04-29 175229](https://github.com/user-attachments/assets/3f6e7267-40d5-49ae-90ba-578e01a08f56)



**Question 6**
---
![Screenshot 2025-04-29 175239](https://github.com/user-attachments/assets/7796d297-cde9-4e67-b954-f500b9ffbd6e)


```sql
SELECT 
    c.*
FROM 
    customer c
LEFT JOIN 
    orders o ON c.customer_id = o.customer_id
WHERE 
    o.ord_date BETWEEN '2012-08-01' AND '2012-08-30';

```

**Output:**

![Screenshot 2025-04-29 175248](https://github.com/user-attachments/assets/0a707ca0-2e01-4687-acd2-fff961e4e9e2)


**Question 7**
---
![Screenshot 2025-04-29 175300](https://github.com/user-attachments/assets/0d71aaa7-46eb-4840-868d-c712cd75b9e9)


```sql
SELECT 
    p.first_name AS "patient_name",
    t.*
FROM 
    patients p
INNER JOIN 
    test_results t ON p.patient_id = t.patient_id
WHERE 
    t.test_name = 'Blood Pressure';

```

**Output:**

![Screenshot 2025-04-29 175309](https://github.com/user-attachments/assets/61734d02-6db5-4564-8c27-b3eb2b863be7)


**Question 8**
---
![Screenshot 2025-04-29 175322](https://github.com/user-attachments/assets/375f86ca-b58f-4238-b261-64ec028ab153)


```sql
SELECT 
    c.cust_name,
    c.city AS "city",
    c.grade,
    s.name AS "Salesman",
    s.city AS "city"
FROM 
    customer c
JOIN 
    salesman s ON c.salesman_id = s.salesman_id
WHERE 
    c.grade < 300
ORDER BY 
    c.customer_id ASC;

```

**Output:**

![Screenshot 2025-04-29 175333](https://github.com/user-attachments/assets/906be265-e001-4255-8ea9-9af069c59eba)


**Question 9**
![Screenshot 2025-04-29 175347](https://github.com/user-attachments/assets/049ac4fe-4810-40aa-8963-ba4ead92c0ef)


```sql
SELECT 
    p.first_name AS "patient_name",
    t.*
FROM 
    patients p
INNER JOIN 
    test_results t ON p.patient_id = t.patient_id;


```

**Output:**
![Screenshot 2025-04-29 175358](https://github.com/user-attachments/assets/83e3cbee-264e-45b3-b897-3f37fb6cca79)



**Question 10**
---
![Screenshot 2025-04-29 175408](https://github.com/user-attachments/assets/52b73fd0-64e6-4277-a5c8-f18c06d1142f)


```sql
SELECT 
    c.cust_name,
    o.ord_no,
    o.ord_date,
    o.purch_amt
FROM 
    customer c
LEFT JOIN 
    orders o ON c.customer_id = o.customer_id;

```

**Output:**

![Screenshot 2025-04-29 175421](https://github.com/user-attachments/assets/e1017772-3dc8-45f6-b998-ec59a0a159c1)



## RESULT
Thus, the SQL queries to implement different types of joins have been executed successfully.
