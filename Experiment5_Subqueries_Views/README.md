# Experiment 5: Subqueries and Views

## AIM
To study and implement subqueries and views.

## THEORY

### Subqueries
A subquery is a query inside another SQL query and is embedded in:
- WHERE clause
- HAVING clause
- FROM clause

**Types:**
- **Single-row subquery**:
  Sub queries can also return more than one value. Such results should be made use along with the operators in and any.
- **Multiple-row subquery**:
  Here more than one subquery is used. These multiple sub queries are combined by means of ‘and’ & ‘or’ keywords.
- **Correlated subquery**:
  A subquery is evaluated once for the entire parent statement whereas a correlated Sub query is evaluated once per row processed by the parent statement.

**Example:**
```sql
SELECT * FROM employees
WHERE salary > (SELECT AVG(salary) FROM employees);
```
### Views
A view is a virtual table based on the result of an SQL SELECT query.
**Create View:**
```sql
CREATE VIEW view_name AS
SELECT column1, column2 FROM table_name WHERE condition;
```
**Drop View:**
```sql
DROP VIEW view_name;
```

**Question 1**
--
<img width="1148" height="714" alt="image" src="https://github.com/user-attachments/assets/b4413445-b54b-448e-8c32-8d0904a16522" />


```sql
SELECT *
FROM customer
WHERE customer_id = (
    SELECT salesman_id - 2001
    FROM salesman
    WHERE name = 'Mc Lyon'
);
```

**Output:**

<img width="1234" height="425" alt="image" src="https://github.com/user-attachments/assets/6fde600e-75d6-4889-a580-131423104b15" />


**Question 2**
---



```sql
<img width="1028" height="691" alt="image" src="https://github.com/user-attachments/assets/e166844c-5580-48ac-ac07-a10f3d28c82f" />

```

**Output:**

<img width="1214" height="445" alt="image" src="https://github.com/user-attachments/assets/369a0686-d84c-41af-8f5f-0e5938d8f009" />

**Question 3**
---
<img width="1231" height="473" alt="image" src="https://github.com/user-attachments/assets/327d5c59-7168-452b-b3ee-b8f4af723b59" />


```sql
SELECT *
FROM Departments
WHERE LENGTH(department_name) >
(
    SELECT AVG(LENGTH(department_name))
    FROM Departments
);
```

**Output:**

<img width="662" height="502" alt="image" src="https://github.com/user-attachments/assets/020c7cbe-d8b4-4d39-a8c0-bd64437048e0" />


**Question 4**
---
<img width="1192" height="641" alt="image" src="https://github.com/user-attachments/assets/5cd451db-30a4-4a19-86ad-5f481bcf1f2d" />


```sql

SELECT ord_no, purch_amt, ord_date, customer_id, salesman_id
FROM orders
WHERE salesman_id =
(
    SELECT salesman_id
    FROM salesman
    WHERE name = 'Paul Adam'
);
```

**Output:**

<img width="1219" height="439" alt="image" src="https://github.com/user-attachments/assets/14e3a3e6-351d-4d59-a419-24d741988428" />

**Question 5**
---
<img width="1170" height="683" alt="image" src="https://github.com/user-attachments/assets/55763d7d-1c61-485f-9214-394e2d7ddcde" />


```sql
SELECT commission
FROM salesman
WHERE salesman_id IN
(
    SELECT salesman_id
    FROM customer
    WHERE city = 'Paris'
);
```

**Output:**

<img width="511" height="469" alt="image" src="https://github.com/user-attachments/assets/f0ff12d0-e41b-4a8e-a78e-9a781f8a9760" />


**Question 6**
---
<img width="982" height="619" alt="image" src="https://github.com/user-attachments/assets/fa924f2b-2937-403d-9066-51a5ff0ceadf" />


```sql


SELECT *
FROM CUSTOMERS
WHERE ADDRESS = 'Delhi';
```

**Output:**
<img width="1226" height="372" alt="image" src="https://github.com/user-attachments/assets/de5ea145-6607-48f5-a4db-7807dd62da07" />


**Question 7**
---
<img width="1267" height="668" alt="image" src="https://github.com/user-attachments/assets/bc1ed89e-89c0-4d48-b734-91d1ee10ff39" />


```sql

SELECT ord_no, purch_amt, ord_date, customer_id, salesman_id
FROM orders
WHERE salesman_id IN
(
    SELECT salesman_id
    FROM salesman
    WHERE city = 'London'
);
```

**Output:**

<img width="1247" height="573" alt="image" src="https://github.com/user-attachments/assets/6de1161b-d7cf-4da9-beeb-5951868e5eb7" />


**Question 8**
---
<img width="1241" height="773" alt="image" src="https://github.com/user-attachments/assets/41c9a969-ee71-4805-926a-cc7b59c66d79" />


```sql
SELECT *
FROM CUSTOMERS
WHERE AGE < 30;
```

**Output:**

<img width="1252" height="672" alt="image" src="https://github.com/user-attachments/assets/be415d6d-5d48-445d-99e5-fedc09cc70b2" />


**Question 9**
---
<img width="1223" height="665" alt="image" src="https://github.com/user-attachments/assets/fdbf50b7-6790-4556-9f36-f45d3e8457ce" />


```sql
SELECT *
FROM GRADES g1
WHERE grade =
(
    SELECT MAX(g2.grade)
    FROM GRADES g2
    WHERE g1.subject = g2.subject
);
```

**Output:**

<img width="1219" height="516" alt="image" src="https://github.com/user-attachments/assets/ea37192a-26e0-48c5-b0a7-612c38706759" />


**Question 10**
---
<img width="1231" height="744" alt="image" src="https://github.com/user-attachments/assets/cd0b89bc-dac4-4e58-a8db-781465de50b5" />


```sql


SELECT s.salesman_id, s.name
FROM salesman s
JOIN customer c
ON s.salesman_id = c.salesman_id
GROUP BY s.salesman_id, s.name
HAVING COUNT(c.customer_id) > 1;
```

**Output:**

<img width="879" height="608" alt="image" src="https://github.com/user-attachments/assets/27eef1e6-e9ac-4769-bcc5-c5b285d8ba80" />



## RESULT
Thus, the SQL queries to implement subqueries and views have been executed successfully.
