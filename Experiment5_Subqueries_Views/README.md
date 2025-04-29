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
Write a SQL query to retrieve all columns from the CUSTOMERS table for customers whose Address as Delhi

Sample table: CUSTOMERS

![image](https://github.com/user-attachments/assets/9774a61f-1eb2-4e53-bf1f-f229dc5f9b28)




```sql
SELECT * FROM Customers
WHERE ADDRESS = 'Delhi';
```

**Output:**

![image](https://github.com/user-attachments/assets/4628bed7-8249-4a09-b24e-7cd10eadcbcc)


**Question 2**
---
Write a SQL query that retrieve all the columns from the table "Grades", where the grade is equal to the maximum grade achieved in each subject.

Sample table: GRADES (attributes: student_id, student_name, subject, grade)

![image](https://github.com/user-attachments/assets/ea7a840d-4929-42a2-836a-097668cee699)


```sql
SELECT *
FROM Grades g
WHERE grade = (
    SELECT MAX(grade)
    FROM Grades
    WHERE subject = g.subject
);

```

**Output:**

![image](https://github.com/user-attachments/assets/5150f1bb-420f-4e76-9c6a-e2f3f98e697f)


**Question 3**
---
Write a SQL query to retrieve all columns from the CUSTOMERS table for customers whose salary is LESS than $2500.

Sample table: CUSTOMERS

![image](https://github.com/user-attachments/assets/1b5cbf01-243b-400d-aee2-b77be8ba6dc0)

```sql
SELECT * FROM CUSTOMERS
WHERE SALARY < 2500;
```

**Output:**

![image](https://github.com/user-attachments/assets/fea9a726-06b7-4782-9187-3c78d520cad2)


**Question 4**
---
Write a SQL query to Find employees who have an age less than the average age of employees with incomes over 1 million

Employee Table

![image](https://github.com/user-attachments/assets/5e6a1ccf-c80c-4ee3-a553-993f677efc6a)


```sql
SELECT *
FROM Employee
WHERE age < (
SELECT AVG(age)
FROM Employee
WHERE income > 1000000);

```

**Output:**

![image](https://github.com/user-attachments/assets/c8d4ecd5-1a58-4405-a8f5-9c4e2c0e9579)


**Question 5**
---
From the following tables, write a SQL query to find those salespeople who earned the maximum commission. Return ord_no, purch_amt, ord_date, and salesman_id.

salesman table

![image](https://github.com/user-attachments/assets/1ce23f15-650c-47b1-8986-bb15b0d83a37)


```sql
SELECT ord_no, purch_amt, ord_date, salesman_id
FROM orders
WHERE salesman_id IN (
    SELECT salesman_id
    FROM salesman
    WHERE commission = (SELECT MAX(commission) FROM salesman)
);

```

**Output:**

![image](https://github.com/user-attachments/assets/291f45d4-5d4d-49ef-8da9-27eb762c1111)


**Question 6**
---
Write a SQL query to Retrieve the medications with dosages equal to the lowest dosage

Table Name: Medications (attributes: medication_id, medication_name, dosage)

![image](https://github.com/user-attachments/assets/b3802cfc-4920-4d94-92b7-c95541d3da80)


```sql
SELECT *
FROM Medications
WHERE dosage = (SELECT MIN(dosage) FROM Medications);

```

**Output:**

![image](https://github.com/user-attachments/assets/f08c6441-74e3-4043-a43a-bf1712f042b9)


**Question 7**
---
Write a SQL query that retrieves the all the columns from the Table Grades, where the grade is equal to the minimum grade achieved in each subject.

Sample table: GRADES (attributes: student_id, student_name, subject, grade)

![image](https://github.com/user-attachments/assets/1b12a6f7-4564-437d-a582-9c5574018390)


```sql
SELECT *
FROM Grades g
WHERE grade = (
    SELECT MIN(grade)
    FROM Grades
    WHERE subject = g.subject
);
```

**Output:**

![image](https://github.com/user-attachments/assets/b639da34-2736-468c-8f6a-9a5f86187c87)


**Question 8**
---
From the following tables write a SQL query to find salespeople who had more than one customer. Return salesman_id and name.

salesman table

![image](https://github.com/user-attachments/assets/65881e1e-4b25-41cb-8608-97b351f1e040)





```sql
SELECT salesman_id, name
FROM SALESMAN
WHERE salesman_id IN (
    SELECT salesman_id
    FROM CUSTOMER
    GROUP BY salesman_id
    HAVING COUNT(customer_id) > 1
);

```

**Output:**

![image](https://github.com/user-attachments/assets/9c224ba4-7afb-4979-a014-74d37ac97c28)



**Question 9**
---
Write a SQL query to retrieve all columns from the CUSTOMERS table for customers whose Address as Delhi and age below 30

Sample table: CUSTOMERS

![image](https://github.com/user-attachments/assets/9aca90f6-6fc9-43b5-bb0e-6c5f08d96902)


```sql
select ID,NAME,AGE,ADDRESS,SALARY
from CUSTOMERS
where ID in (select ID from CUSTOMERS
where ADDRESS='Delhi' );
```

**Output:**

![image](https://github.com/user-attachments/assets/6c44b3ae-be21-47aa-aab6-6dc550ca8ca4)

**Question 10**
---
Write a query to display all the customers whose ID is the difference between the salesperson ID of Mc Lyon and 2001.

![image](https://github.com/user-attachments/assets/0ee06b1f-993a-4bea-9e52-56bcd7647c20)


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

![image](https://github.com/user-attachments/assets/a9d05cbf-6cdc-42ec-8815-1dbb9fc78470)



## RESULT
Thus, the SQL queries to implement subqueries and views have been executed successfully.
