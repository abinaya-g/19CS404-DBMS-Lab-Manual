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

Write the SQL query that achieves the selection of the first name from the "patients" table (aliased as "patient_name") and the first name from the "doctors" table (aliased as "doctor_name"), with an inner join on the "doctor_id" column and a condition filtering for patients with a date of birth after '1990-01-01'.

PATIENTS TABLE:

ATTRIBUTES - patient_id, first_name, last_name, date_of_birth, admission_date, discharge_date, doctor_id

![Screenshot 2025-05-14 131006](https://github.com/user-attachments/assets/4e6c1c1e-0e45-4bd9-9059-4f20eda29683)


DOCTORS TABLE:

ATTRIBUTES - doctor_id, first_name, last_name, specialization

![Screenshot 2025-05-14 131011](https://github.com/user-attachments/assets/55df11e3-8d45-46c9-8a6d-42bd4a34fbe4)

~~~
SELECT p.first_name as "patient_name",d.first_name as "doctor_name"
FROM patients p
INNER JOIN DOCTORS d on p.doctor_id = d.doctor_id
WHERE p.date_of_birth > "1990-01-01";
~~~

**Output:**

![Screenshot 2025-05-14 134723](https://github.com/user-attachments/assets/ef5566bc-d639-4a75-9bb1-edb94e718bf3)


**Question 2**

Write a SQL statement to make a report with customer name, city, order number, order date, and order amount in ascending order according to the order date to determine whether any of the existing customers have placed an order or not.
~~~
Sample table: orders

ord_no      purch_amt   ord_date    customer_id  salesman_id
----------  ----------  ----------  -----------  -----------
70001       150.5       2012-10-05  3005         5002
70009       270.65      2012-09-10  3001         5005
70002       65.26       2012-10-05  3002         5001
70004       110.5       2012-08-17  3009         5003
70007       948.5       2012-09-10  3005         5002
70005       2400.6      2012-07-27  3007         5001
70008       5760        2012-09-10  3002         5001
70010       1983.43     2012-10-10  3004         5006
70003       2480.4      2012-10-10  3009         5003
70012       250.45      2012-06-27  3008         5002
70011       75.29       2012-08-17  3003         5007
70013       3045.6      2012-04-25  3002         5001

Sample table: customer

 customer_id |   cust_name    |    city    | grade | salesman_id 
-------------+----------------+------------+-------+-------------
        3002 | Nick Rimando   | New York   |   100 |        5001
        3007 | Brad Davis     | New York   |   200 |        5001
        3005 | Graham Zusi    | California |   200 |        5002
        3008 | Julian Green   | London     |   300 |        5002
        3004 | Fabian Johnson | Paris      |   300 |        5006
        3009 | Geoff Cameron  | Berlin     |   100 |        5003
        3003 | Jozy Altidor   | Moscow     |   200 |        5007
~~~
~~~
SELECT 
    c.cust_name, 
    c.city, 
    o.ord_no, 
    o.ord_date, 
    o.purch_amt AS "Order Amount"
FROM customer c  
LEFT JOIN orders o ON c.customer_id = o.customer_id  
ORDER BY o.ord_date ASC;
~~~

**Output:**

![Screenshot 2025-05-14 134953](https://github.com/user-attachments/assets/ce3d0130-899b-4a23-8a0b-f1768db976f5)


**Question 3**

QL statement to generate a report with customer name, city, order number, order date, order amount, salesperson name, and commission to determine if any of the existing customers have not placed orders or if they have placed orders through their salesman or by themselves.
~~~
Sample table: customer

 customer_id |   cust_name    |    city    | grade | salesman_id 
-------------+----------------+------------+-------+-------------
        3002 | Nick Rimando   | New York   |   100 |        5001
        3007 | Brad Davis     | New York   |   200 |        5001
        3005 | Graham Zusi    | California |   200 |        5002
        3008 | Julian Green   | London     |   300 |        5002
        3004 | Fabian Johnson | Paris      |   300 |        5006
        3009 | Geoff Cameron  | Berlin     |   100 |        5003
        3003 | Jozy Altidor   | Moscow     |   200 |        5007
        3001 | Brad Guzan     | London     |       |        5005

Sample table: orders

ord_no      purch_amt   ord_date    customer_id  salesman_id
----------  ----------  ----------  -----------  -----------
70001       150.5       2012-10-05  3005         5002
70009       270.65      2012-09-10  3001         5005
70002       65.26       2012-10-05  3002         5001
70004       110.5       2012-08-17  3009         5003
70007       948.5       2012-09-10  3005         5002
70005       2400.6      2012-07-27  3007         5001
70008       5760        2012-09-10  3002         5001
70010       1983.43     2012-10-10  3004         5006
70003       2480.4      2012-10-10  3009         5003
70012       250.45      2012-06-27  3008         5002
70011       75.29       2012-08-17  3003         5007
70013       3045.6      2012-04-25  3002         5001

Sample table: salesman

 salesman_id |    name    |   city   | commission 
-------------+------------+----------+------------
        5001 | James Hoog | New York |       0.15
        5002 | Nail Knite | Paris    |       0.13
        5005 | Pit Alex   | London   |       0.11
        5006 | Mc Lyon    | Paris    |       0.14
        5007 | Paul Adam  | Rome     |       0.13
        5003 | Lauson Hen | San Jose |       0.12
~~~
~~~
SELECT 
    c.cust_name, 
    c.city, 
    o.ord_no , 
    o.ord_date, 
    o.purch_amt as "Order Amount", 
    s.name AS name, 
    s.commission  
FROM customer c  
LEFT JOIN orders o ON c.customer_id = o.customer_id  
LEFT JOIN salesman s ON o.salesman_id = s.salesman_id ;
~~~

**Output:**

![Screenshot 2025-05-14 135125](https://github.com/user-attachments/assets/a18b5b4c-0023-4554-a9e6-c7bb8fcb7e9a)


**Question 4**
Write the SQL query that achieves the selection of the first name from the "patients" table (aliased as "patient_name"), with an inner join on the "doctor_id" column and conditions filtering for patients whose doctor has the first name 'Emily', last name 'Johnson', and a non-null discharge date.

PATIENTS TABLE:

ATTRIBUTES - patient_id, first_name, last_name, date_of_birth, admission_date, discharge_date, doctor_id

![Screenshot 2025-05-14 135711](https://github.com/user-attachments/assets/6b7bf182-85f8-46b9-8dc9-a36160a7e9ab)

DOCTORS TABLE:

ATTRIBUTES - doctor_id, first_name, last_name, specialization

![Screenshot 2025-05-14 135716](https://github.com/user-attachments/assets/0a7674bc-55e8-4609-9d23-ba21b199b456)
~~~
SELECT p.first_name AS patient_name  
FROM patients p  
INNER JOIN doctors d ON p.doctor_id = d.doctor_id  
WHERE d.first_name = 'Emily' 
  AND d.last_name = 'Johnson' 
  AND p.discharge_date IS NOT NULL;
~~~

**Output:**

![image](https://github.com/user-attachments/assets/0dcfab10-b205-4385-ab77-624519698090)

**Question 5**

Write a SQL statement to join the tables salesman, customer and orders so that the same column of each table appears once and only the relational rows are returned. 
~~~
Sample table: orders

ord_no      purch_amt   ord_date    customer_id  salesman_id
----------  ----------  ----------  -----------  -----------
70001       150.5       2012-10-05  3005         5002
70009       270.65      2012-09-10  3001         5005
70002       65.26       2012-10-05  3002         5001
70004       110.5       2012-08-17  3009         5003
70007       948.5       2012-09-10  3005         5002
70005       2400.6      2012-07-27  3007         5001
70008       5760        2012-09-10  3002         5001
70010       1983.43     2012-10-10  3004         5006
70003       2480.4      2012-10-10  3009         5003
70012       250.45      2012-06-27  3008         5002
70011       75.29       2012-08-17  3003         5007
70013       3045.6      2012-04-25  3002         5001

Sample table: customer

 customer_id |   cust_name    |    city    | grade | salesman_id 
-------------+----------------+------------+-------+-------------
        3002 | Nick Rimando   | New York   |   100 |        5001
        3007 | Brad Davis     | New York   |   200 |        5001
        3005 | Graham Zusi    | California |   200 |        5002
        3008 | Julian Green   | London     |   300 |        5002
        3004 | Fabian Johnson | Paris      |   300 |        5006
        3009 | Geoff Cameron  | Berlin     |   100 |        5003
        3003 | Jozy Altidor   | Moscow     |   200 |        5007
        3001 | Brad Guzan     | London     |       |        5005

Sample table : salesman

 salesman_id |    name    |   city   | commission 
-------------+------------+----------+------------
        5001 | James Hoog | New York |       0.15
        5002 | Nail Knite | Paris    |       0.13
        5005 | Pit Alex   | London   |       0.11
        5006 | Mc Lyon    | Paris    |       0.14
        5007 | Paul Adam  | Rome     |       0.13
        5003 | Lauson Hen | San Jose |       0.12
~~~
~~~
SELECT 
    o.ord_no, 
    o.purch_amt, 
    o.ord_date, 
    c.cust_name, 
    c.city AS customer_city, 
    c.grade, 
    s.name AS salesman_name, 
    s.city AS salesman_city, 
    s.commission  
FROM orders o  
INNER JOIN customer c ON o.customer_id = c.customer_id  
INNER JOIN salesman s ON o.salesman_id = s.salesman_id;
~~~

**Output:**

![Screenshot 2025-05-14 140026](https://github.com/user-attachments/assets/8b87ee72-aee4-4ea1-a016-1d07501cbcbd)


**Question 6**
~~~
From the following tables write a SQL query to find those customers with a grade less than 300. Return cust_name, customer city, grade, Salesman, salesmancity. The result should be ordered by ascending customer_id. 

Sample table: customer

 customer_id |   cust_name    |    city    | grade | salesman_id 
-------------+----------------+------------+-------+-------------
        3002 | Nick Rimando   | New York   |   100 |        5001
        3007 | Brad Davis     | New York   |   200 |        5001
        3005 | Graham Zusi    | California |   200 |        5002
        3008 | Julian Green   | London     |   300 |        5002
        3004 | Fabian Johnson | Paris      |   300 |        5006
        3009 | Geoff Cameron  | Berlin     |   100 |        5003
        3003 | Jozy Altidor   | Moscow     |   200 |        5007
        3001 | Brad Guzan     | London     |       |        5005

Sample table: salesman

 salesman_id |    name    |   city   | commission 
-------------+------------+----------+------------
        5001 | James Hoog | New York |       0.15
        5002 | Nail Knite | Paris    |       0.13
        5005 | Pit Alex   | London   |       0.11
        5006 | Mc Lyon    | Paris    |       0.14
        5007 | Paul Adam  | Rome     |       0.13
        5003 | Lauson Hen | San Jose |       0.12
~~~
~~~
SELECT 
    c.cust_name, 
    c.city AS "city", 
    c.grade, 
    s.name AS Salesman, 
    s.city AS city  
FROM customer c  
INNER JOIN salesman s ON c.salesman_id = s.salesman_id  
WHERE c.grade < 300  
ORDER BY c.customer_id ASC;

~~~
**Output:**

![Screenshot 2025-05-14 140139](https://github.com/user-attachments/assets/030e5b32-2eda-425a-ae60-9023fc2c95ed)

**Question 7**

Write the SQL query that achieves the selection of all columns from the "customer" table (aliased as "c"), with a left join on the "customer_id" column and a condition filtering for orders with an order date later than '2012-08-17'.

CUSTOMER TABLE:

![Screenshot 2025-05-14 140403](https://github.com/user-attachments/assets/c38fa7e6-f8e7-4eda-b0b4-aec8d2a47adc)

ORDERS TABLE:

![Screenshot 2025-05-14 140408](https://github.com/user-attachments/assets/2898d2c1-9b49-4da0-a88b-cfbbc2feb9de)

~~~
SELECT 
    c.* 
FROM customer c  
LEFT JOIN orders o ON c.customer_id = o.customer_id  
WHERE o.ord_date > '2012-08-17';
~~~

**Output:**

![Screenshot 2025-05-14 140439](https://github.com/user-attachments/assets/be18e55f-217c-4a33-9302-05f2cff0ac4b)

**Question 8**
Write the SQL query that achieves the selection of the "name" column from the "salesman" table (aliased as "s"), with a left join on the "salesman_id" column and a condition filtering for customers in the city 'London'.

Customer Table:

![Screenshot 2025-05-14 140611](https://github.com/user-attachments/assets/b3f82cee-3231-4204-9b19-c3e55bb8804f)

Salesmen Table:

![Screenshot 2025-05-14 140616](https://github.com/user-attachments/assets/f246355e-cc1b-4637-8aed-3245acf7e7c3)

~~~
SELECT 
    s.name 
FROM salesman s 
LEFT JOIN customer c ON s.salesman_id = c.salesman_id 
WHERE c.city = 'London';
~~~

**Output:**

![Screenshot 2025-05-14 140713](https://github.com/user-attachments/assets/7cf42cb8-fb1e-48d1-81ca-970290bca24e)

**Question 9**

From the following tables write a SQL query to find those orders where the order amount exists between 500 and 2000. Return ord_no, purch_amt, cust_name, city.

~~~
Sample table: customer

 customer_id |   cust_name    |    city    | grade | salesman_id 
-------------+----------------+------------+-------+-------------
        3002 | Nick Rimando   | New York   |   100 |        5001
        3007 | Brad Davis     | New York   |   200 |        5001
        3005 | Graham Zusi    | California |   200 |        5002
        3008 | Julian Green   | London     |   300 |        5002
        3004 | Fabian Johnson | Paris      |   300 |        5006
        3009 | Geoff Cameron  | Berlin     |   100 |        5003
        3003 | Jozy Altidor   | Moscow     |   200 |        5007
        3001 | Brad Guzan     | London     |       |        5005

Sample table: orders

ord_no      purch_amt   ord_date    customer_id  salesman_id
----------  ----------  ----------  -----------  -----------
70001       150.5       2012-10-05  3005         5002
70009       270.65      2012-09-10  3001         5005
70002       65.26       2012-10-05  3002         5001
70004       110.5       2012-08-17  3009         5003
70007       948.5       2012-09-10  3005         5002
70005       2400.6      2012-07-27  3007         5001
70008       5760        2012-09-10  3002         5001
70010       1983.43     2012-10-10  3004         5006
70003       2480.4      2012-10-10  3009         5003
70012       250.45      2012-06-27  3008         5002
70011       75.29       2012-08-17  3003         5007
70013       3045.6      2012-04-25  3002         5001
~~~
~~~
SELECT 
    o.ord_no, 
    o.purch_amt, 
    c.cust_name, 
    c.city 
FROM orders o 
JOIN customer c ON o.customer_id = c.customer_id 
WHERE o.purch_amt BETWEEN 500 AND 2000;

~~~
**Output:**

![Screenshot 2025-05-14 140817](https://github.com/user-attachments/assets/92be5b0a-7da2-46f1-aac1-c3fc51dba7c7)

**Question 10**

Write the SQL query that achieves the selection of the first name from the "patients" table, with an inner join on the "patient_id" column and a condition filtering for surgeries with a surgery date of '2024-01-15'.:

~~~
PATIENTS TABLE:

name             type
---------------  ---------------
patient_id       INT
first_name       VARCHAR(50)
last_name        VARCHAR(50)
date_of_birth    DATE
admission_date   DATE
discharge_date   DATE
doctor_id        INT

SURGERIES TABLE:

name             type
---------------  ---------------
surgery_id       INT
patient_id       INT
surgeon_id       INT
surgery_date     DATE
~~~
~~~
SELECT p.first_name
FROM PATIENTS p
INNER JOIN SURGERIES s on p.patient_id = s.patient_id
WHERE s.surgery_date = '2024-01-15';
~~~

**Output:**

![Screenshot 2025-05-14 140954](https://github.com/user-attachments/assets/8cebc937-974b-4527-aa83-71502cef8b92)

## RESULT
Thus, the SQL queries to implement different types of joins have been executed successfully.
