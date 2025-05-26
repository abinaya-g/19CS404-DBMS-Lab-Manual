# Experiment 3: DML Commands

## AIM
To study and implement DML (Data Manipulation Language) commands.

## THEORY

### 1. INSERT INTO
Used to add records into a relation.
These are three type of INSERT INTO queries which are as
A)Inserting a single record
**Syntax (Single Row):**
```sql
INSERT INTO table_name (field_1, field_2, ...) VALUES (value_1, value_2, ...);
```
**Syntax (Multiple Rows):**
```sql
INSERT INTO table_name (field_1, field_2, ...) VALUES
(value_1, value_2, ...),
(value_3, value_4, ...);
```
**Syntax (Insert from another table):**
```sql
INSERT INTO table_name SELECT * FROM other_table WHERE condition;
```
### 2. UPDATE
Used to modify records in a relation.
Syntax:
```sql
UPDATE table_name SET column1 = value1, column2 = value2 WHERE condition;
```
### 3. DELETE
Used to delete records from a relation.
**Syntax (All rows):**
```sql
DELETE FROM table_name;
```
**Syntax (Specific condition):**
```sql
DELETE FROM table_name WHERE condition;
```
### 4. SELECT
Used to retrieve records from a table.
**Syntax:**
```sql
SELECT column1, column2 FROM table_name WHERE condition;
```
**Question 1**
--
Write a SQL statement to change the first_name column of employees table with 'John' for those employees whose department_id is 80 and gets a commission_pct below 0.35.

```sql
update EMPLOYEES set first_name = "John" where department_id = 80 and commission_pct < .35;
```

**Output:**

![image](https://github.com/user-attachments/assets/246583e1-c637-4b47-a140-a12a6dd53871)

**Question 2**
---
Write a SQL statement to update the product_name as 'Grapefruit' whose product_id is 4 in the products table.

```sql
update products set product_name = "Grapefruit" where product_id = 4;
```

**Output:**
![image](https://github.com/user-attachments/assets/81148570-0140-4836-9dba-24c12d67f032)

**Question 3**
---
Write a SQL query to Delete All Doctors whose ID ranges from 2 to 4.

```sql
delete from Doctors where doctor_id between 2 and 4;
```

**Output:**

![image](https://github.com/user-attachments/assets/44b75600-fdb6-4884-b6c6-b7b8594dc772)

**Question 4**
---
Write a SQL query to Delete customers with following conditions

* 'CUST_COUNTRY' is not in a list of specified countries ('UK', 'USA', 'Canada')
* 'GRADE' is greater than or equal to 3

```sql
delete from Customer where cust_country not in ('UK', 'USA', 'Canada') and grade >= 3
```

**Output:**
![image](https://github.com/user-attachments/assets/0fec7b3c-b4a6-4b1f-bb59-0f6250acfd44)

**Question 5**
---
Write a SQL statement to change the EMAIL and COMMISSION_PCT column of the following EMPLOYEES table with 'not available' and 0.55 for those employees whose DEPARTMENT_ID is 110.

```sql
update employees set email = 'not available', commission_pct = 0.55 where department_id=110;
```

**Output:**
![image](https://github.com/user-attachments/assets/4d3b0c1f-5fc2-4bac-ae8e-2e8babd8a526)


**Question 6**
---
Write a SQL statement to Find the salesmen with all information who gets the commission within a range of 0.12 and 0.14.

```sql
select * from salesman where commission between 0.12 and 0.14;
```

**Output:**

![image](https://github.com/user-attachments/assets/c216330a-e369-4dc1-8b89-2b9fe0235e8b)

**Question 7**
---
Write a SQL statement to Find those salesmen with all information whose name containing the 1st character is 'N' and the 4th character is 'l' and rests may be any character.

```sql
select * from salesman where name like 'N__l%';
```

**Output:**
![image](https://github.com/user-attachments/assets/65d2e588-ff0e-436e-852a-298a79abc143)

**Question 8**
---
Write a SQL query to assign a priority of 'Low', 'Medium', or 'High' to value2 based on whether it is less than 20, between 20 and 50, or greater than 50, respectively in the Calculations table.

```sql
select id,value2, 
case
    when value2 < 20 then 'Low'
    when value2 between 20 and 50 then 'Medium'
    when value2 > 50 then 'High'
    end as priority from Calculations;
```

**Output:**

![image](https://github.com/user-attachments/assets/ae61d350-fc6d-4178-b037-c1f823dda408)

**Question 9**
---
Write a SQL query to calculate the absolute value of the value1 column from the Calculations table.

```sql
select id,value1,abs(value1) as absolute_value from Calculations;
```

**Output:**

![image](https://github.com/user-attachments/assets/5a12a686-465e-4ace-84b9-7261faed914c)


**Question 10**
---
Write a SQL query to select orders between 500 and 4000 (begin and end values are included). Exclude orders amount 948.50 and 1983.43. Return ord_no, purch_amt, ord_date, customer_id, and salesman_id.

```sql
select ord_no, purch_amt, ord_date, customer_id, salesman_id from orders 
where purch_amt between 500 and 4000
and purch_amt not in (948.50, 1983.43);
```

**Output:**

![image](https://github.com/user-attachments/assets/297e3a2c-befd-44bb-9859-e49167733639)

## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.

## PROOF
![image](https://github.com/user-attachments/assets/16d20e12-d446-424d-890b-965a58e34af0)
