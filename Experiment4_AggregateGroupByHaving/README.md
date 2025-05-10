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
How many patients have insurance coverage valid in each year?

Sample table:Insurance Table

![image](https://github.com/user-attachments/assets/a3c1b350-c27d-4a4e-b58c-5bfeac0ee015)

Query :
```sql
SELECT strftime('%Y',ValidityPeriod) AS "ValidityYear",COUNT(PatientID) AS "TotalPatients"
FROM Insurance
GROUP BY ValidityPeriod;
```

**Output:**

![image](https://github.com/user-attachments/assets/8946fbc9-9b25-4b6c-afd5-4fcfd7a4b8f2)


**Question 2**
---
What is the average dosage prescribed for each medication?

Sample table : Prescriptions Table

![image](https://github.com/user-attachments/assets/46071368-20c3-4420-b379-685c8e30bebd)

Query :
```sql
SELECT Medication,Avg(Dosage) AS "AvgDosage"
FROM Prescriptions
GROUP BY Medication;
```

**Output:**

![image](https://github.com/user-attachments/assets/284b2375-0ce4-4095-8884-1944ef6fbbc5)


**Question 3**
---
What is the total number of medications prescribed for each patient?

Sample table : Prescriptions Table

![image](https://github.com/user-attachments/assets/97f724ad-71d4-459b-a4de-35d5f57c5ff2)

Query :
```sql
SELECT PatientID,COUNT(Medication) AS "TotalMedications"
FROM Prescriptions
GROUP BY PatientID;
```

**Output:**

![image](https://github.com/user-attachments/assets/cb100246-21c8-4939-949a-e5ba6f77ea96)


**Question 4**
---
Write a SQL query to Calculate the average income of the employees with names starting with 'A': 

Table: employee

![image](https://github.com/user-attachments/assets/1aaf76f2-374c-4a19-9da9-a62949f1ade4)

Query :
```sql
SELECT AVG(income) AS avg_income
FROM employee
WHERE name LIKE 'A%';
```

**Output:**

![image](https://github.com/user-attachments/assets/75580b3d-c969-4d37-914d-2d0f08dd2546)


**Question 5**
---
Write a SQL query to find What is the age difference between the youngest and oldest employee in the company.

Table: employee

![image](https://github.com/user-attachments/assets/615ebbba-1883-46be-8740-8756d2a140d2)

Query :
```sql
SELECT MAX(AGE)-MIN(AGE) AS "age_difference"
FROM employee;
```

**Output:**

![image](https://github.com/user-attachments/assets/646dbd3d-24bb-4cfd-8acd-7f07021eb413)


**Question 6**
---
Write a SQL query that counts the number of unique salespeople. Return number of salespeople.

Sample table: orders

![image](https://github.com/user-attachments/assets/555375b3-b668-40a8-b231-5e549aecd2cc)

Query :
```sql
SELECT COUNT(DISTINCT salesman_id) AS "COUNT"
FROM orders;
```

**Output:**

![image](https://github.com/user-attachments/assets/346f2b3a-e8a5-45cb-a8d0-65fddb2b7492)


**Question 7**
---
Write a SQL query to find how many employees have an income greater than 50K?

Table: employee

![image](https://github.com/user-attachments/assets/06c4129e-153f-44d6-8666-0a177d96bfa5)

Query :
```sql
SELECT COUNT(id) AS "employees_count"
FROM employee
WHERE income > 50000;
```

**Output:**

![image](https://github.com/user-attachments/assets/dcff847c-4a01-4765-9ea9-9094e73bb65e)

**Question 8**
---
Write the SQL query that accomplishes the grouping of data by joining date (jdate), calculates the minimum work hours for each date, and excludes dates where the minimum work hour is not less than 10.

Sample table: employee1

![image](https://github.com/user-attachments/assets/fd22bb7b-429c-45f4-9822-8958c9b609b3)

Query :
```sql
SELECT jdate,MIN(workhour) AS "MIN(workhour)"
FROM employee1
GROUP BY jdate
HAVING MIN(workhour) < 10;
```

**Output:**

![image](https://github.com/user-attachments/assets/0b8a51a5-2b7d-434e-8bd7-865a76647410)

**Question 9**
---
Write the SQL query that achieves the grouping of data by age, calculates the minimum income for each age group, and includes only those age groups where the minimum income is less than 400,000.

Sample table: employee

![image](https://github.com/user-attachments/assets/2fb804bf-6c7d-425f-a627-f87619a0e6a4)

Query :
```sql
SELECT age,MIN(income) AS "MIN(income)"
FROM employee
GROUP BY age
Having MIN(income) < 400000;
```

**Output:**


![image](https://github.com/user-attachments/assets/7e631007-d5ba-482d-8493-2b7d8116fa5a)


**Question 10**
---
Write the SQL query that achieves the grouping of data by occupation, calculates the minimum work hours for each occupation, and excludes occupations where the minimum work hour is not greater than 8.

Sample table: employee1


![image](https://github.com/user-attachments/assets/49d16088-ec0f-4401-a1dc-2e252ae2259c)

Query :
```sql
SELECT occupation,MIN(workhour) AS "MIN(workhour)"
FROM employee1
GROUP BY occupation
HAVING MIN(workhour)  > 8;
```

**Output:**



![image](https://github.com/user-attachments/assets/9e75389b-1def-472d-9aba-1a211bbe9b32)

## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
