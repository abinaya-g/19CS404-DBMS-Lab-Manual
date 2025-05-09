# NAME: BALA B
# REG NO: 212224100005
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
-- ![Screenshot 2025-04-29 152109](https://github.com/user-attachments/assets/a80f9552-f113-474d-9f1c-9a239f4e8c81)


```sql
--SELECT 
    p.first_name AS patient_name,
    t.test_name
FROM 
    patients p
INNER JOIN 
    test_results t ON p.patient_id = t.patient_id;

```

**Output:**

![Screenshot 2025-04-29 152117](https://github.com/user-attachments/assets/8549fcb9-e1f7-4b0e-8f4e-361e95a9a093)


**Question 2**
---
-- ![Screenshot 2025-04-29 152215](https://github.com/user-attachments/assets/d53405bc-6cd0-4029-a7ea-1984bc3ce1cd)


```sql
-- SELECT 
    s.name,
    c.cust_name,
    c.city,
    c.grade,
    c.salesman_id
FROM 
    salesman s
LEFT JOIN 
    customer c ON s.salesman_id = c.salesman_id
WHERE 
    s.salesman_id IN (
        SELECT salesman_id
        FROM customer
        GROUP BY salesman_id
        HAVING COUNT(*) > 1
    );

```

**Output:**

![Screenshot 2025-04-29 152220](https://github.com/user-attachments/assets/53e8980f-89f1-4ed6-8c8f-557232aa408d)


**Question 3**
---
-- ![Screenshot 2025-04-29 152308](https://github.com/user-attachments/assets/1d9d2279-0f34-4b69-9f7e-abd724fedb17)


```sql
-- SELECT 
    o.ord_no,
    o.purch_amt,
    o.ord_date,
    c.cust_name,
    c.city AS customer_city,
    c.grade,
    s.name AS salesman_name,
    s.city AS salesman_city,
    s.commission
FROM 
    orders o
INNER JOIN 
    customer c ON o.customer_id = c.customer_id
INNER JOIN 
    salesman s ON o.salesman_id = s.salesman_id;

```

**Output:**

![Screenshot 2025-04-29 152316](https://github.com/user-attachments/assets/0fd3efb7-0f76-4275-87f6-cc76a47234fd)


**Question 4**
---
-- ![Screenshot 2025-04-29 152356](https://github.com/user-attachments/assets/d67a9e2a-239b-4170-8455-6b1730247a78)


```sql
--SELECT 
    n.nurse_id,
    d.department_name
FROM 
    nurses n
INNER JOIN 
    departments d ON n.department_id = d.department_id
WHERE 
    n.first_name = 'David'
    AND n.last_name = 'Moore';

```

**Output:**

![Screenshot 2025-04-29 152401](https://github.com/user-attachments/assets/1c6d1c61-0039-4b89-8f01-d191c692e747)


**Question 5**
---
-- ![Screenshot 2025-04-29 152443](https://github.com/user-attachments/assets/54e12e5e-dec7-47b5-9abe-7b76577cfe45)


```sql
-- SELECT 
    c.cust_name AS "Customer Name",
    c.city AS "city",
    s.name AS "Salesman",
    s.city AS "city",
    s.commission
FROM 
    customer c
INNER JOIN 
    salesman s ON c.salesman_id = s.salesman_id
WHERE 
    c.city <> s.city
    AND s.commission > 0.12;

```

**Output:**

![Screenshot 2025-04-29 152449](https://github.com/user-attachments/assets/0a3704b8-01a4-459c-935b-ca34ee6cf09d)

**Question 6**
---
-- ![Screenshot 2025-04-29 152534](https://github.com/user-attachments/assets/9940ce44-864e-47db-a345-b0ac97081317)


```sql
-- SELECT 
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
    salesman s ON o.salesman_id = s.salesman_id;

```

**Output:**

![Screenshot 2025-04-29 152543](https://github.com/user-attachments/assets/0895455c-4c01-448f-a24a-676488bcab06)

**Question 7**
---
-- ![Screenshot 2025-04-29 152642](https://github.com/user-attachments/assets/f30a9092-2125-4477-9f21-c925cfc178e3)


```sql
--SELECT 
    p.*
FROM 
    patients p
INNER JOIN 
    test_results t ON p.patient_id = t.patient_id
WHERE 
    t.test_name = 'X-Ray'
    AND t.result = 'Normal';

```

**Output:**

![Screenshot 2025-04-29 152648](https://github.com/user-attachments/assets/19551591-e9e5-4aba-ade1-9d1a4b9d3598)


**Question 8**
---
-- ![Screenshot 2025-04-29 152729](https://github.com/user-attachments/assets/5f7ae7a0-69ed-4372-8ac8-81e22955be8a)


```sql
-- SELECT 
    c.cust_name,
    c.city,
    o.ord_no,
    o.ord_date,
    o.purch_amt AS "Order Amount"
FROM 
    customer c
LEFT JOIN 
    orders o ON c.customer_id = o.customer_id
ORDER BY 
    o.ord_date ASC;

```

**Output:**

![Screenshot 2025-04-29 152735](https://github.com/user-attachments/assets/dee7a7c4-5bc1-4e15-8c4a-c299e99bd8b7)


**Question 9**
---
-- ![image](https://github.com/user-attachments/assets/559cfb24-807b-4d37-bca4-c7237a15e202)


```sql
-- SELECT 
    c.cust_name,
    s.name
FROM 
    customer c
LEFT JOIN 
    salesman s ON c.salesman_id = s.salesman_id
WHERE 
    c.city = s.city;

```

**Output:**

![Screenshot 2025-04-29 152843](https://github.com/user-attachments/assets/057478a1-1f4e-4c38-a601-639a854a7132)


**Question 10**
---
-- ![Screenshot 2025-04-29 152915](https://github.com/user-attachments/assets/b4f99a81-f280-4c30-939b-daaebc56f634)


```sql
--SELECT 
    c.cust_name AS "Customer Name",
    c.city AS "city",
    s.name AS "Salesman",
    s.commission AS "commission"
FROM 
    customer c
JOIN 
    salesman s ON c.salesman_id = s.salesman_id;

```

**Output:**

![Screenshot 2025-04-29 152922](https://github.com/user-attachments/assets/7f8e1354-169d-40f6-a772-01c3b80620dd)



## RESULT
Thus, the SQL queries to implement different types of joins have been executed successfully.****
