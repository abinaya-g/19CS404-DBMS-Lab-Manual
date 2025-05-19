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

Write SQL query to extract the email domain from each patient's email address and count the number of patients with the same email domain.

Sample table: Patients Table

![Screenshot 2025-04-30 155825](https://github.com/user-attachments/assets/6a0b3dbb-312a-4550-a9c1-d47584a3a91c)
~~~
SELECT SUBSTR(email,INSTR(email,'@')+1) AS EmailDomain,COUNT(*) AS TotalPatients
FROM Patients
GROUP BY EmailDomain;
~~~


**Output:**


![Screenshot 2025-04-30 155913](https://github.com/user-attachments/assets/541d59ac-05a6-4ddc-a98d-cc874e20ca32)


**Question 2**

How many prescriptions were written by each doctor?

Sample tablePrescriptions Table


![Screenshot 2025-04-30 160008](https://github.com/user-attachments/assets/e8e17029-4ffd-4309-99ff-93ee71df6ebe)

~~~
SELECT DoctorID, COUNT(*) AS TotalPrescriptions FROM Prescriptions
GROUP BY DoctorID;
~~~
**Output:**

![Screenshot 2025-04-30 160119](https://github.com/user-attachments/assets/99a0c958-4fba-40f0-ad05-c8146ae73636)


**Question 3**

Write a SQL Query to find how many medications are prescribed for each patient?

Sample table:MedicalRecords Table

![Screenshot 2025-04-30 160214](https://github.com/user-attachments/assets/e5eb3770-f29c-4a93-b216-0f5ec5792713)

~~~
SELECT PatientID, COUNT(*) AS AvgMedications
FROM MedicalRecords
GROUP BY PatientID;
~~~

**Output:**


![Screenshot 2025-04-30 160301](https://github.com/user-attachments/assets/dd342735-b786-4c91-97a2-6ed1f00988dc)


**Question 4**
~~~
Write a SQL query to  find the average salary of all employees?

Table: employee

name        type
----------  ----------
id          INTEGER
name        TEXT
age         INTEGER
city        TEXT
income      INTEGER
~~~
~~~
SELECT AVG(income) AS Average_Salary
FROM employee;
~~~
**Output:**

![Screenshot 2025-04-30 160359](https://github.com/user-attachments/assets/cc438a84-b656-4dec-ab33-5d26f33e102b)


**Question 5**
Write a SQL query to return the total number of rows in the 'customer' table where the city is not Noida.

Sample table: customer

![Screenshot 2025-04-30 160446](https://github.com/user-attachments/assets/db24316b-4071-4445-a4c5-2a9da9d78636)
~~~
SELECT COUNT(*) AS COUNT
FROM customer
WHERE city NOT IN('Noida');
~~~

**Output:**

![Screenshot 2025-04-30 160525](https://github.com/user-attachments/assets/58a0b6b5-4b4b-4c17-9281-8f44b0ecb172)


**Question 6**
~~~
Write a SQL query to find the Fruit with the lowest available quantity.

Note: Inventory attribute contains amount of fruits

Table: fruits

name        type
----------  ----------
id          INTEGER
name        TEXT
unit        TEXT
inventory   INTEGER
price       REAL
~~~
~~~
SELECT name AS fruit_name,inventory AS lowest_quantity FROM fruits
ORDER BY inventory ASC
LIMIT 1;
~~~

**Output:**


![Screenshot 2025-04-30 160633](https://github.com/user-attachments/assets/8e6a778c-eeff-4988-8353-d6d508fd09e4)


**Question 7**
~~~
Write a SQL query that counts the number of unique salespeople. Return number of salespeople.

Sample table: orders

ord_no      purch_amt   ord_date    customer_id  salesman_id

----------  ----------  ----------  -----------  -----------

70001       150.5       2012-10-05  3005         5002

70009       270.65      2012-09-10  3001         5005

70002       65.26       2012-10-05  3002         5001
~~~
~~~
SELECT COUNT(DISTINCT salesman_id) AS COUNT
FROM orders;
~~~

**Output:**


![Screenshot 2025-04-30 160732](https://github.com/user-attachments/assets/158cc1e9-ab8a-4ef0-891a-fa3b2d477b96)


**Question 8**
Write the SQL query that accomplishes the selection of total number of products for each category from the "products" table, and includes only those products where the minimum category ID is less than 3.

Sample table: products

![Screenshot 2025-04-30 160810](https://github.com/user-attachments/assets/b2692566-7773-468d-be70-f116df2f731a)

~~~
SELECT category_id, count(product_name)
FROM products
WHERE category_id <3
GROUP BY category_id;
~~~

**Output:**

![Screenshot 2025-04-30 160855](https://github.com/user-attachments/assets/40f10715-18bf-420a-93a1-b5bace66a762)


**Question 9**
Write the SQL query that accomplishes the grouping of data by joining date (jdate), calculates the total work hours for each date, and excludes dates where the total work hour sum is not greater than 40.

Sample table: employee1

![Screenshot 2025-04-30 160926](https://github.com/user-attachments/assets/6251de96-b45f-4c53-92ef-467229652899)

~~~
select jdate,SUM(workhour) as "SUM(workhour)"
from employee1
group by jdate
having SUM(workhour) >40;
~~~

**Output:**


![Screenshot 2025-04-30 161013](https://github.com/user-attachments/assets/7d1b3832-a0ab-414b-b3fb-0e9731032167)


**Question 10**
Write the SQL query that achieves the grouping of data by age, calculates the minimum income for each age group, and includes only those age groups where the minimum income is less than 1,000,000.

Sample table: employee


![Screenshot 2025-04-30 161052](https://github.com/user-attachments/assets/019cad5b-f49a-4d3f-9d0b-c8675b432436)

~~~
select age , MIN(Income) AS 'Income'
from employee
group by age
having MIN(Income)<1000000;
~~~
**Output:**


![Screenshot 2025-04-30 161144](https://github.com/user-attachments/assets/a8fec4f2-f452-4082-97bf-0f99334ae94a)



## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
