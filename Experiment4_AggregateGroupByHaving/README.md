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
How many medical records are there for each patient?

```sql
select PatientID,count(*) as TotalRecords from MedicalRecords group by PatientID;
```

**Output:**

![image](https://github.com/user-attachments/assets/3a65ce4e-eae4-411a-a048-af8ce875c9af)


**Question 2**
---
Write a SQL Query to find how many medications are prescribed for each patient?

```sql
select PatientID, count(Medications) as AvgMedications from MedicalRecords group by PatientID;
```

**Output:**

![image](https://github.com/user-attachments/assets/69c4b3c0-10ed-44d3-8475-0b497d2fe2fb)


**Question 3**
---
How many appointments are scheduled in each hour of the day?

```sql
select strftime('%H',AppointmentDateTime) as HourOfDay, count(*) as TotalAppointments from Appointments group by HourOfDay;
```

**Output:**

![image](https://github.com/user-attachments/assets/087c9be1-12fd-4b17-ad20-154280b274be)


**Question 4**
---
Write a SQL query that counts the number of unique salespeople. Return number of salespeople.

```sql
select count(distinct salesman_id) as COUNT from orders;
```

**Output:**

![image](https://github.com/user-attachments/assets/c34457df-85f7-4b86-9819-26015c535894)


**Question 5**
---
Write a SQL query to  find the average salary of all employees?

```sql
select avg(income) as Average_Salary from employee;
```

**Output:**

![image](https://github.com/user-attachments/assets/0fffcde1-89f9-447b-ad59-e6e812c5cbe2)


**Question 6**
---
Write a SQL query to find the total amount of fruits with a unit type of 'LB'.

```sql
select sum(inventory) as total from fruits where unit="LB";
```

**Output:**

![image](https://github.com/user-attachments/assets/d1a5e248-9ec5-470a-b1a8-dd18123889de)


**Question 7**
---
Write a SQL query to count the number of customers. Return number of customers.

```sql
select count(customer_id) as COUNT from customer;
```

**Output:**

![image](https://github.com/user-attachments/assets/2f4248a5-1886-4fb6-8e1e-1c82a255b98e)


**Question 8**
---
Write the SQL query that accomplishes the selection of total cost of all products in each category from the "products" table and includes only those products where the total cost is greater than 50.

```sql
select category_id, sum(price) as Total_Cost from products group by category_id having Total_Cost>50;
```

**Output:**

![image](https://github.com/user-attachments/assets/030f5772-481f-4f57-a853-f01ccf600cd2)


**Question 9**
---
Write the SQL query that accomplishes the selection of number of products for each category from products table which includes only those products where the category ID is greater than 2.

```sql
select category_id,count(product_name) as COUNT from products group by category_id having category_id > 2;
```

**Output:**

![image](https://github.com/user-attachments/assets/8447519f-1ee9-4400-8def-574796f0b661)


**Question 10**
---
Write the SQL query that accomplishes the selection of product which has lowest price in each category from the "products" table and includes only those products where the minimum price is less than 10.

```sql
select category_id, min(Price) as Price from products group by category_id having Price < 10;
```

**Output:**

![image](https://github.com/user-attachments/assets/0ae9125c-0155-4dab-a2da-4bea8bc2c1fc)



## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
