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
How many appointments are scheduled in each hour of the day?

Sample table:Appointments Table

name                              type
--------------------          ----------
AppointmentID               INTEGER
PatientID                   INTEGER
DoctorID                    INTEGER
AppointmentDateTime         DATETIME
Purpose                     TEXT
Status                      TEXT
```sql
SELECT 
    strftime('%H', AppointmentDateTime) AS HourOfDay,
    COUNT(*) AS TotalAppointments
FROM Appointments
GROUP BY strftime('%H', AppointmentDateTime)
ORDER BY HourOfDay;
```

**Output:**

<img width="1229" height="602" alt="image" src="https://github.com/user-attachments/assets/40a68fc3-c41b-4656-95ee-c7a5287553a2" />


**Question 2**
---
What is the total number of appointments scheduled for each day?

Table: Appointments

name                 type
-------------------  ----------
AppointmentID        INTEGER
PatientID            INTEGER
DoctorID             INTEGER
AppointmentDateTime  DATETIME
Purpose              TEXT
Status               TEXT

```sql
SELECT 
    DATE(AppointmentDateTime) AS AppointmentDate,
    COUNT(*) AS TotalAppointments
FROM Appointments
GROUP BY DATE(AppointmentDateTime)
ORDER BY AppointmentDate;
```

**Output:**

<img width="1221" height="730" alt="image" src="https://github.com/user-attachments/assets/1a22dde1-49da-4a47-9620-aa40fbc549d7" />

**Question 3**
---
How many medical records does each doctor have?

Sample table:MedicalRecords Table



```sql
SELECT 
    DoctorID,
    COUNT(*) AS TotalRecords
FROM MedicalRecords
GROUP BY DoctorID
ORDER BY DoctorID;
```

**Output:**

<img width="1216" height="699" alt="image" src="https://github.com/user-attachments/assets/cffe9606-7065-4d7c-b095-9f82364cc03f" />


**Question 4**
---
Write a SQL query to find the number of employees who are having the same age removing the duplicate values.

Sample table: employee

id

name

age

address

salary

1

Paul

32

California

20000

4

Mark

25

Richtown

65000

5

David

27

Texas

85000



```sql
SELECT COUNT(DISTINCT age) AS COUNT
FROM employee;
```

**Output:**

<img width="1205" height="375" alt="image" src="https://github.com/user-attachments/assets/701753ea-036a-4c94-bebe-79cb29c588f4" />

**Question 5**
---
Write a SQL query to find the maximum purchase amount.

Sample table: orders

ord_no      purch_amt   ord_date    customer_id  salesman_id

----------  ----------  ----------  -----------  -----------

70001       150.5       2012-10-05  3005         5002

70009       270.65      2012-09-10  3001         5005

70002       65.26       2012-10-05  3002         5001

```sql
SELECT 
    MAX(purch_amt) AS MAXIMUM
FROM orders;
```

**Output:**

<img width="1210" height="379" alt="image" src="https://github.com/user-attachments/assets/49936adf-68b6-4746-abd7-9bd1f309af3a" />


**Question 6**
---
Write a SQL query to calculate the total number of working hours of all employees

Sample table: employee1

```sql
SELECT 
    SUM(workhour) AS "Total working hours"
FROM employee1;
```

**Output:**

<img width="1220" height="369" alt="image" src="https://github.com/user-attachments/assets/7850a241-2eec-4574-be95-60bf3315fd33" />


**Question 7**
---
Write a SQL query to determine the number of customers who received at least one grade for their activity.

Sample table: customer

customer_id |   cust_name    |    city    | grade | salesman_id 

-------------+----------------+------------+-------+-------------

        3002 | Nick Rimando   | New York   |   100 |        5001

        3007 | Brad Davis     | New York   |   200 |        5001

        3005 | Graham Zusi    | California |   200 |        5002

```sql
SELECT 
    COUNT(*) AS COUNT
FROM customer
WHERE grade IS NOT NULL;
```

**Output:**

<img width="1226" height="373" alt="image" src="https://github.com/user-attachments/assets/58c5116e-eea9-4176-b844-0fceaacb84d9" />


**Question 8**
---
Write the SQL query that achieves the grouping of data by age, calculates the minimum income for each age group, and includes only those age groups where the minimum income is less than 1,000,000.

Sample table: employee

```sql
SELECT 
    age,
    MIN(income) AS Income
FROM employee
GROUP BY age
HAVING MIN(income) < 1000000;
```

**Output:**

<img width="1222" height="496" alt="image" src="https://github.com/user-attachments/assets/ff063fe3-cc25-42ce-a6ad-ca699352ab7f" />


**Question 9**
---
Write the SQL query that accomplishes the grouping of data by joining date (jdate), calculates the minimum work hours for each date, and excludes dates where the minimum work hour is not less than 10.

Sample table: employee1



```sql
SELECT 
    jdate,
    MIN(workhour) AS "MIN(workhour)"
FROM employee1
GROUP BY jdate
HAVING MIN(workhour) < 10;
```

**Output:**

<img width="1216" height="498" alt="image" src="https://github.com/user-attachments/assets/67ad7466-89c1-40dd-99f6-e87827789d2a" />


**Question 10**
---
Write the SQL query that accomplishes the selection of total cost of all products in each category from the "products" table and includes only those products where the total cost is greater than 50.

Sample table: products
```sql
SELECT 
    category_id,
    SUM(price) AS Total_Cost
FROM products
GROUP BY category_id
HAVING SUM(price) > 50;
```

**Output:**

<img width="1208" height="395" alt="image" src="https://github.com/user-attachments/assets/50ba8057-6f33-4747-be04-8466d16d4fd2" />
**GRADE**
<img width="770" height="606" alt="image" src="https://github.com/user-attachments/assets/0adcd825-2546-4c37-8294-a121e404b067" />


## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
