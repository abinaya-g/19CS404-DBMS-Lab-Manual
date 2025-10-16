# Experiment 3: DML Commands

## DEVOLOPED BY:MARXIN LIJO M
## REGISTER NUMBER:212223240085

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

![image](https://github.com/user-attachments/assets/3fb5b196-fd57-4e9c-8d03-4e445dacb453)


```sql
UPDATE products
SET product_name = 'Grapefruit'
WHERE product_id = 4;
```

**Output:**

![image](https://github.com/user-attachments/assets/450e752a-8c92-4174-94ef-f60a21dce154)


**Question 2**

![image](https://github.com/user-attachments/assets/58478acf-17ff-41bf-805b-a990e525e4a8)


```sql
UPDATE employees
SET salary = salary * 2
WHERE department_id = 20
  AND job_id LIKE '%MAN';
```

**Output:**

![image](https://github.com/user-attachments/assets/cd7d0fc7-ea44-4d43-aae0-0d8f5c592dde)

**Question 3**

![image](https://github.com/user-attachments/assets/a5cc9cd3-1df5-443d-b76b-55953b47d747)


```sql
UPDATE SALES
SET sell_price = sell_price + 3
WHERE product_id IN (
    SELECT product_id 
    FROM PRODUCTS 
    WHERE supplier_id = 4
);
```

**Output:**

![image](https://github.com/user-attachments/assets/4154d858-e973-4537-aa69-9f77dcad49e9)


**Question 4**

![image](https://github.com/user-attachments/assets/aa005081-072e-4412-8adb-6f500afeb345)


```sql
UPDATE sales
SET total_sell_price = quantity * sell_price
WHERE product_id = 10;
```

**Output:**

![image](https://github.com/user-attachments/assets/a8ddecbd-e86a-480f-b302-3c8e0bdec3a5)


**Question 5**

![image](https://github.com/user-attachments/assets/4851b1e3-8122-4449-85f2-a87cf346ca0a)


```sql
UPDATE employees
SET email = 'Unavailable';
```

**Output:**

![image](https://github.com/user-attachments/assets/61fe882b-be3b-4d18-9d74-055e18806cbe)


**Question 6**

![image](https://github.com/user-attachments/assets/cf249de4-51d1-4571-b684-3cbcabf18f1e)


```sql
DELETE FROM customer
WHERE GRADE = 2;
```

**Output:**

![image](https://github.com/user-attachments/assets/b3b16aa3-a2d2-4974-9955-ed1a57cd9156)

**Question 7**

![image](https://github.com/user-attachments/assets/4065dd95-30d9-43f4-a790-ff72adce9e33)


```sql
DELETE FROM customer
WHERE CUST_COUNTRY NOT IN ('India', 'USA');
```

**Output:**

![image](https://github.com/user-attachments/assets/f4560ca2-1fbc-476d-b647-33d71db7d372)


**Question 8**

![image](https://github.com/user-attachments/assets/7f7a74a1-870f-4a1f-8b31-df3bc457e045)


```sql
DELETE FROM customer
WHERE GRADE >= 2;
```

**Output:**

![image](https://github.com/user-attachments/assets/1e0da64d-81c1-4493-aed7-9e30ea6eef28)


**Question 9**

![image](https://github.com/user-attachments/assets/6582b276-3672-4426-b317-7549c9b32a9d)


```sql
DELETE FROM Doctors
WHERE specialization = 'Pediatrics'
  AND first_name = 'Michael';
```

**Output:**

![image](https://github.com/user-attachments/assets/2d9ca326-978a-42e2-a707-7b52de0a1324)

**Question 10**

![image](https://github.com/user-attachments/assets/5cdc5453-a0c6-4290-b442-dffb772c27e9)


```sql
DELETE FROM customer
WHERE AGENT_CODE IN ('A003', 'A008');
```

**Output:**

![image](https://github.com/user-attachments/assets/46f39bd1-21b8-4724-b47b-53099e272de6)

## GRADE

<img width="1367" height="78" alt="image" src="https://github.com/user-attachments/assets/a6857546-979c-47c5-8980-1f95e6345155" />



## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
