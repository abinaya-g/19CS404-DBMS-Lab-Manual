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
<img width="1232" height="799" alt="image" src="https://github.com/user-attachments/assets/eea04385-57d5-497f-8642-71761d02a09c" />


```sql


SELECT p.first_name, s.*
FROM patients p
INNER JOIN surgeries s
ON p.patient_id = s.patient_id
WHERE p.date_of_birth > '1990-01-01';
```

**Output:**
<img width="1246" height="486" alt="image" src="https://github.com/user-attachments/assets/ed5030fa-7970-4629-bee3-4206054604ae" />


**Question 2**
---
<img width="1226" height="1001" alt="image" src="https://github.com/user-attachments/assets/43ddee0d-6760-4610-8400-26becae07cf0" />


```sql


SELECT o.ord_no,
       o.ord_date,
       o.purch_amt,
       c.cust_name AS "Customer Name",
       c.grade,
       s.name AS "Salesman",
       s.commission
FROM orders o
INNER JOIN customer c
ON o.customer_id = c.customer_id
INNER JOIN salesman s
ON o.salesman_id = s.salesman_id;
```

**Output:**

<img width="1245" height="1029" alt="image" src="https://github.com/user-attachments/assets/77e23a78-5b17-43d7-a09b-2b2b71cbbd61" />

**Question 3**
---
<img width="1233" height="923" alt="image" src="https://github.com/user-attachments/assets/582a0432-6f34-4bfd-ada0-c81cb6480798" />


```sql


SELECT p.admission_date,
       s.surgery_date
FROM patients p
INNER JOIN surgeries s
ON p.patient_id = s.patient_id;
```

**Output:**

<img width="874" height="647" alt="image" src="https://github.com/user-attachments/assets/5ca63521-9fa6-48e1-8fbf-d3bd00449335" />

**Question 4**
---
<img width="1236" height="828" alt="image" src="https://github.com/user-attachments/assets/97bb0172-5442-4f59-8a44-b0f8ef296ec3" />


```
SELECT p.first_name,
       s.*
FROM patients p
INNER JOIN surgeries s
ON p.patient_id = s.patient_id
WHERE p.discharge_date BETWEEN '2024-03-01' AND '2024-03-31'
AND p.admission_date NOT BETWEEN '2024-03-01' AND '2024-03-31';
```

**Output:**
<img width="1283" height="553" alt="image" src="https://github.com/user-attachments/assets/f30e6cc2-4ae6-4941-9b45-1d6dd253ebfe" />



**Question 5**

---

<img width="1264" height="876" alt="image" src="https://github.com/user-attachments/assets/9cc4fc53-ff45-4468-92aa-6be42d3393de" />




```sql

SELECT s.name,
       c.cust_name,
       c.city,
       c.grade,
       c.salesman_id
FROM salesman s
LEFT JOIN customer c
ON s.salesman_id = c.salesman_id;
```

**Output:**

<img width="1217" height="888" alt="image" src="https://github.com/user-attachments/assets/3784bd7e-46dc-4b0a-bbaa-7d3ae8dc34ab" />


**Question 6**
---
<img width="1240" height="835" alt="image" src="https://github.com/user-attachments/assets/f6ed721e-b037-43ed-9f41-57d202d27081" />


```sql

SELECT p.first_name AS patient_name,
       d.specialization AS Doctor_specialization
FROM patients p
INNER JOIN doctors d
ON p.doctor_id = d.doctor_id
WHERE p.admission_date BETWEEN '2024-01-01' AND '2024-01-31';
```

**Output:**

<img width="913" height="497" alt="image" src="https://github.com/user-attachments/assets/2343f24a-7ec6-426e-aed8-5de3751ce620" />


**Question 7**
---
<img width="1196" height="682" alt="image" src="https://github.com/user-attachments/assets/3dc1c262-4c6c-4fd6-9b1d-45f00abf67e4" />


```sql


SELECT p.first_name AS patient_name,
       t.*
FROM patients p
INNER JOIN test_results t
ON p.patient_id = t.patient_id;
```

**Output:**

<img width="1238" height="602" alt="image" src="https://github.com/user-attachments/assets/653fac59-ecb0-475a-bbfc-9d181841cb2c" />


**Question 8**
---

<img width="1240" height="1033" alt="image" src="https://github.com/user-attachments/assets/f0c0adbc-1749-4268-ae73-48cc7e1f54c4" />


```sql


SELECT c.cust_name,
       c.city,
       o.ord_no,
       o.ord_date,
       o.purch_amt AS "Order Amount",
       s.name,
       s.commission
FROM customer c
LEFT JOIN orders o
ON c.customer_id = o.customer_id
LEFT JOIN salesman s
ON c.salesman_id = s.salesman_id;
```

**Output:**

<img width="1198" height="1039" alt="image" src="https://github.com/user-attachments/assets/bb1f1c7c-a9a7-415b-8a7e-b99a888e3e56" />


**Question 9**
---

<img width="1241" height="666" alt="image" src="https://github.com/user-attachments/assets/01cf6ddc-60f4-4885-bc77-e211b1a383ff" />


```sql
SELECT t.*
FROM test_results t
INNER JOIN patients p
ON t.patient_id = p.patient_id
WHERE p.first_name = 'Alice';
```

**Output:**

<img width="1225" height="475" alt="image" src="https://github.com/user-attachments/assets/be00e76d-8a58-4eca-a2ac-aabcd8657ff0" />


**Question 10**
---
<img width="1227" height="941" alt="image" src="https://github.com/user-attachments/assets/b15f6bcc-1556-4e34-a5e1-d5df7ab10741" />


```sql


SELECT c.cust_name,
       o.ord_no,
       o.ord_date,
       o.purch_amt
FROM customer c
LEFT JOIN orders o
ON c.customer_id = o.customer_id;
```

**Output:**

<img width="1208" height="1023" alt="image" src="https://github.com/user-attachments/assets/e6df5427-f13f-4b57-8c06-9228301cd7a2" />



## RESULT
Thus, the SQL queries to implement different types of joins have been executed successfully.
