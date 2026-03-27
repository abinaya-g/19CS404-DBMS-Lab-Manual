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
Write a SQL query to retrieve all columns from the CUSTOMERS table for customers whose AGE is LESS than $30

Sample table: CUSTOMERS

ID          NAME        AGE         ADDRESS     SALARY
----------  ----------  ----------  ----------  ----------

1          Ramesh     32              Ahmedabad     2000
2          Khilan        25              Delhi                 1500
3          Kaushik      23              Kota                  2000
4          Chaitali       25             Mumbai            6500
5          Hardik        27              Bhopal              8500
6          Komal         22              Hyderabad       4500

7           Muffy          24              Indore            10000



```sql
select * from CUSTOMERS where AGE<30;
```

**Output:**

<img width="1280" height="652" alt="image" src="https://github.com/user-attachments/assets/9de19065-7bce-4fde-b38c-5da9948431b4" />


**Question 2**
---
Write a query to display all the customers whose ID is the difference between the salesperson ID of Mc Lyon and 2001.

salesman table

name             type
---------------  ---------------
salesman_id      numeric(5)
name                 varchar(30)
city                    varchar(15)
commission       decimal(5,2)

customer table

name         type
-----------  ----------
customer_id  int
cust_name    text
city         text
grade        int
salesman_id  int

```sql
select *
from customer
where customer_id =(
    select salesman_id -2001
    from salesman
    where name='Mc Lyon'
);
```

**Output:**

<img width="1274" height="374" alt="image" src="https://github.com/user-attachments/assets/8af76bce-4d40-4de5-b60f-4914e91ce825" />


**Question 3**
---
Write a SQL query to retrieve all columns from the CUSTOMERS table for customers whose salary is EQUAL TO $1500.

Sample table: CUSTOMERS

ID          NAME        AGE         ADDRESS     SALARY
----------  ----------  ----------  ----------  ----------

1          Ramesh     32              Ahmedabad     2000
2          Khilan        25              Delhi                 1500
3          Kaushik      23              Kota                  2000
4          Chaitali       25             Mumbai            6500
5          Hardik        27              Bhopal              8500
6          Komal         22              Hyderabad       4500

7           Muffy          24              Indore            10000

```sql
select * from CUSTOMERS where salary=1500;
```

**Output:**

<img width="1278" height="398" alt="image" src="https://github.com/user-attachments/assets/52a657e8-2cbc-473a-8534-7d1c20c9a93e" />

**Question 4**
---
Write a SQL query to retrieve all columns from the CUSTOMERS table for customers whose salary is LESS than $2500.

Sample table: CUSTOMERS

ID          NAME        AGE         ADDRESS     SALARY
----------  ----------  ----------  ----------  ----------

1          Ramesh     32              Ahmedabad     2000
2          Khilan        25              Delhi                 1500
3          Kaushik      23              Kota                  2000
4          Chaitali       25             Mumbai            6500
5          Hardik        27              Bhopal              8500
6          Komal         22              Hyderabad       4500

7           Muffy          24              Indore            10000

```sql
select * from CUSTOMERS
where salary<2500;
```

**Output:**

<img width="1286" height="526" alt="image" src="https://github.com/user-attachments/assets/deee2652-fa37-4e28-96bd-4009a795042d" />


**Question 5**
---
From the following tables, write a SQL query to find all the orders generated in New York city. Return ord_no, purch_amt, ord_date, customer_id and salesman_id.

SALESMAN TABLE

name               type
-----------        ----------
salesman_id  numeric(5)
name             varchar(30)
city                 varchar(15)
commission   decimal(5,2)

ORDERS TABLE

name            type
----------      ----------
ord_no          int
purch_amt    real
ord_date       text
customer_id  int
salesman_id  int
```sql
select ord_no, purch_amt, ord_date, customer_id, salesman_id
from ORDERS
where salesman_id in(
    select salesman_id
    from salesman
    where city='New York'
);
```

**Output:**

<img width="1269" height="542" alt="image" src="https://github.com/user-attachments/assets/a23bc2f6-8639-4629-9b4d-186b57e47a75" />

**Question 6**
---
Write a SQL query that retrieves the names of students and their corresponding grades, where the grade is equal to the minimum grade achieved in each subject.

Sample table: GRADES (attributes: student_id, student_name, subject, grade)

```sql
select student_name,grade
from GRADES g
where grade=(
    select MIN(grade)
    from GRADES
    where subject=g.subject
);
```

**Output:**

<img width="1272" height="507" alt="image" src="https://github.com/user-attachments/assets/42fcd379-a9a8-4e91-96c7-792d7e4b298e" />


**Question 7**
---
From the following tables write a SQL query to find all orders generated by London-based salespeople. Return ord_no, purch_amt, ord_date, customer_id, salesman_id.

salesman table

name             type
---------------  ---------------
salesman_id      numeric(5)
name                 varchar(30)
city                    varchar(15)
commission       decimal(5,2)

orders table

name             type
---------------  --------
order_no         int
purch_amt        real
order_date       text
customer_id      int
salesman_id      int

```sql
select ord_no, purch_amt, ord_date, customer_id, salesman_id
from ORDERS
where salesman_id in(
    select salesman_id
    from salesman
    where city='London'
);
```

**Output:**

<img width="1272" height="474" alt="image" src="https://github.com/user-attachments/assets/c6843368-5e5b-4a27-9103-bcfc2a24eef9" />


**Question 8**
---
Write a SQL query to retrieve all columns from the CUSTOMERS table for customers whose Address as Delhi and age below 30

Sample table: CUSTOMERS

ID          NAME        AGE         ADDRESS     SALARY
----------  ----------  ----------  ----------  ----------

1          Ramesh     32              Ahmedabad     2000
2          Khilan        25              Delhi                 1500
3          Kaushik      23              Kota                  2000
4          Chaitali       25             Mumbai            6500
5          Hardik        27              Bhopal              8500
6          Komal         22              Hyderabad       4500

7           Muffy          24              Indore            10000

```sql
select * from CUSTOMERS
where ADDRESS is 'Delhi' and AGE<30
order by ID;
```

**Output:**

<img width="1277" height="432" alt="image" src="https://github.com/user-attachments/assets/67bc3e0a-1ef5-49ed-86b7-462b054f3144" />


**Question 9**
---
From the following tables, write a SQL query to find all orders generated by the salespeople who may work for customers whose id is 3007. Return ord_no, purch_amt, ord_date, customer_id, salesman_id.

Table Name: orders

name             type
---------------  --------
order_no         int
purch_amt        real
order_date       text
customer_id      int
salesman_id      int

```sql
select * from orders
where salesman_id in(
    select salesman_id
    from orders
    where customer_id=3007
);
```

**Output:**

<img width="1274" height="537" alt="image" src="https://github.com/user-attachments/assets/ca08bde4-cca7-40c8-a25d-cc40fd1606b1" />


**Question 10**
---
From the following tables, write a SQL query to find those salespeople who earned the maximum commission. Return ord_no, purch_amt, ord_date, and salesman_id.

salesman table

name             type
---------------  ---------------
salesman_id      numeric(5)
name                 varchar(30)
city                    varchar(15)
commission       decimal(5,2)

orders table

name             type
---------------  --------
order_no         int
purch_amt        real
order_date       text
customer_id      int
salesman_id      int

```sql
select  ord_no, purch_amt, ord_date, salesman_id
from orders
where salesman_id in(
    select salesman_id 
    from salesman
    where commission=(select MAX(commission) from salesman)
);
```

**Output:**
<img width="1279" height="537" alt="image" src="https://github.com/user-attachments/assets/d3601d0a-f005-44b5-9d68-bd9a5fb65688" />

**GRADE**

<img width="770" height="606" alt="image" src="https://github.com/user-attachments/assets/bfffa1ed-4775-4f90-9d41-395ba9a05bf4" />



## RESULT
Thus, the SQL queries to implement subqueries and views have been executed successfully.
