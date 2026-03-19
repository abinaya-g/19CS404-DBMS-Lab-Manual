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
What is the average dosage prescribed for each medication?

Sample tablePrescriptions Table
```
Medication     AvgDosage
-------------  ----------
Ciprofloxacin  500.0
Doxorubicin    60.0
Ibuprofen      400.0
Levothyroxine  50.0
Lisinopril     10.0
MMR            0.5
Pending        0.0
Prenatal vita  1.0
Sertraline     50.0
Topiramate     25.0
```

```
SELECT
  Medication,
  AVG(Dosage) AS AvgDosage
FROM
  Prescriptions
GROUP BY
  Medication;

```

**Output:**


![Screenshot 2025-04-29 171159](https://github.com/user-attachments/assets/cbf06455-04ba-4d64-899c-19b9f6285e48)

**Question 2**
---
How many patients are there in each city?
```
Sample table: Patients Table

Address     TotalPatients
----------  -------------
Berlin      3
Chicago     4
Mexico      3
```
```
select Address,count(*)
as TotalPatients
from Patients
group by Address
```

**Output:**


![Screenshot 2025-04-29 171804](https://github.com/user-attachments/assets/8d4957fe-fb4f-4c02-a28e-1f6c65c3430c)



**Question 3**
---
Write a SQL Query to find how many medications are prescribed for each patient?

Sample table:MedicalRecords Table
```
PatientID   AvgMedications
----------  --------------
4           5
6           1
7           1
8           3

```
```
SELECT PatientID,COUNT(*) AS 
AvgMedications
FROM MedicalRecords
GROUP BY PatientID;
```

**Output:**


![Screenshot 2025-04-29 172124](https://github.com/user-attachments/assets/03cd9d50-06b5-4812-9c53-729d7557944f)


**Question 4**
---
Write a SQL query to find the maximum purchase amount.

Sample table: orders
```
ord_no      purch_amt   ord_date    customer_id  salesman_id

----------  ----------  ----------  -----------  -----------

70001       150.5       2012-10-05  3005         5002

70009       270.65      2012-09-10  3001         5005

70002       65.26       2012-10-05  3002         5001
```
```
SELECT
  MAX(purch_amt) AS MAXIMUM
FROM
  orders;
```

**Output:**


![Screenshot 2025-04-29 172220](https://github.com/user-attachments/assets/3b0552ba-cb0f-47b2-a14f-4f41e3f13b8a)



**Question 5**
---
Write a SQL query to find the total income of employees aged 40 or above.

Table: employee
```
name        type
----------  ----------
id          INTEGER
name        TEXT
age         INTEGER
city        TEXT
income      INTEGER

```
```
SELECT
  SUM(income) AS total_income
FROM
  employee
WHERE
  age >= 40;
```

**Output:**


![Screenshot 2025-04-29 172310](https://github.com/user-attachments/assets/7dd0627c-5b47-45cd-9da2-b4c8b2308c33)


**Question 6**
---
Write a SQL query to find the number of employees whose age is greater than 32.

Sample table: employee

```
SELECT
  COUNT(*) AS COUNT
FROM
  employee
WHERE
  age > 32;
```

**Output:**


![Screenshot 2025-04-29 172421](https://github.com/user-attachments/assets/facbdbb0-4fdf-4680-a2f2-05496c32ebde)

**Question 7**
---
Write a SQL query to find the average length of names for people living in Chennai?

Table: customer
```
name        type
----------  ----------
id          INTEGER
name        TEXT   
city        TEXT
email       TEXT
phone       INTEGER
```
```
SELECT
  AVG(LENGTH(name)) AS avg_name_length
FROM
  customer
WHERE
  city = 'Chennai';
```

**Output:**


![Screenshot 2025-04-29 172506](https://github.com/user-attachments/assets/d162dc9e-2f89-4e8d-ace5-ffa4b385b7bb)


**Question 8**
---
Write the SQL query that accomplishes the grouping of data by joining date (jdate), calculates the maximum work hours for each date, and excludes dates where the maximum work hour is not greater than 12.

Sample table: employee1
```
jdate       MAX(workhour)
----------  -------------
2004.0      15
2006.0      15
```
```
SELECT
  jdate,
  MAX(workhour) AS "MAX(workhour)"
FROM
  employee1
GROUP BY
  jdate
HAVING
  MAX(workhour) > 12;
```

**Output:**


![Screenshot 2025-04-29 172603](https://github.com/user-attachments/assets/4f18be9a-1667-4bc1-825b-115d62e6f1c9)


**Question 9**
---
Write the SQL query that achieves the grouping of data by occupation, calculates the total work hours for each occupation, and excludes occupations where the total work hour sum is not greater than 20.

Sample table: employee1
```
occupation  SUM(workhour)
----------  -------------
Business    30
Doctor      30
Engineer    24
Teacher     27
```
```
SELECT
  occupation,
  SUM(workhour) AS "SUM(workhour)"
FROM
  employee1
GROUP BY
  occupation
HAVING
  SUM(workhour) > 20;
```

**Output:**


![Screenshot 2025-04-29 172703](https://github.com/user-attachments/assets/ed11db98-a58b-4cb2-934b-49a26899d26b)


**Question 10**
---
Write the SQL query that achieves the grouping of data by occupation, calculates the average work hours for each occupation, and includes only those occupations where the average work hour falls between 10 and 12.

Sample table: employee1

```
occupation  AVG(workhour)
----------  -------------
Business    10.0
Engineer    12.0
```
```
SELECT
  occupation,
  AVG(workhour) AS "AVG(workhour)"
FROM
  employee1
GROUP BY
  occupation
HAVING
  AVG(workhour) BETWEEN 10 AND 12;
```

**Output:**


![Screenshot 2025-04-29 172754](https://github.com/user-attachments/assets/2feda0d6-0e59-4af8-a0b6-15ea0c411c22)




## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
