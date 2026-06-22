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

<img width="1194" height="600" alt="image" src="https://github.com/user-attachments/assets/a57d7965-6513-4c79-ac74-9468181ad0e6" />


```sql
SELECT *
FROM salesman
WHERE commission BETWEEN 0.12 AND 0.14;
```

**Output:**

<img width="1140" height="586" alt="image" src="https://github.com/user-attachments/assets/21f11d9f-e32a-4cb8-9475-44a9c7f4f06e" />


**Question 2**
---

<img width="1194" height="527" alt="image" src="https://github.com/user-attachments/assets/2c127826-b3ef-4de1-8604-89fb71e1e097" />


```sql
UPDATE products
SET reorder_lvl = 20
WHERE quantity < 10
  AND category = 'Snacks';
```

**Output:**


<img width="1227" height="666" alt="image" src="https://github.com/user-attachments/assets/33d2774c-7be9-49f0-867f-0bb9128f582a" />


**Question 3**
---

<img width="1111" height="345" alt="image" src="https://github.com/user-attachments/assets/56912797-5927-4382-9c8d-287778f09f18" />


```sql
UPDATE products
SET sell_price = sell_price * 1.10
WHERE category = 'Bakery';
```

**Output:**

<img width="1230" height="580" alt="image" src="https://github.com/user-attachments/assets/e76ec32b-6e2a-40c0-8021-ebdab8cde36b" />


**Question 4**
---

<img width="1135" height="697" alt="image" src="https://github.com/user-attachments/assets/6523ba95-1018-4d95-a774-d796c727d72c" />


```sql
SELECT name, city
FROM salesman
WHERE city IN ('London', 'Rome');
```

**Output:**

<img width="630" height="421" alt="image" src="https://github.com/user-attachments/assets/c2b3fbdd-6990-44eb-9450-ac723afd94ea" />


**Question 5**
---

<img width="1117" height="837" alt="image" src="https://github.com/user-attachments/assets/dfae0c48-41bb-45de-a6f5-aeb6b04db8ca" />


```sql
UPDATE sales
SET sell_price = sell_price + 3
WHERE product_id IN (
    SELECT product_id
    FROM products
    WHERE supplier_id = 4
);
```

**Output:**

<img width="1215" height="460" alt="image" src="https://github.com/user-attachments/assets/31bd739e-754a-4a65-b134-70a868e0767d" />


**Question 6**
---

<img width="1217" height="626" alt="image" src="https://github.com/user-attachments/assets/c1bc3c82-6bd5-4a9a-8f16-8eec7c7ad7f5" />


```sql
SELECT 
    id,
    value1,
    CASE
        WHEN value1 < 13 THEN 'Child'
        WHEN value1 BETWEEN 13 AND 19 THEN 'Teen'
        ELSE 'Adult'
    END AS age_group
FROM Calculations;
```

**Output:**


<img width="1154" height="402" alt="image" src="https://github.com/user-attachments/assets/5973b197-bfc6-4b8e-a81c-98f41ef6c375" />


**Question 7**
---

<img width="1038" height="341" alt="image" src="https://github.com/user-attachments/assets/e5efcbed-a441-4e92-9808-549a2021582f" />

```sql
UPDATE suppliers
SET supplier_name = 'A1 Suppliers'
WHERE supplier_id = 8;
```

**Output:**

<img width="1231" height="460" alt="image" src="https://github.com/user-attachments/assets/ddbc51bc-019f-4546-b227-7cf41666880d" />


**Question 8**
---

<img width="1205" height="490" alt="image" src="https://github.com/user-attachments/assets/9dfa2477-4439-479d-9c5f-7fe3be7444e5" />


```sql
SELECT *
FROM salesman
WHERE name LIKE 'N__l%';
```

**Output:**


<img width="1233" height="397" alt="image" src="https://github.com/user-attachments/assets/5d792298-cb72-4c68-8760-6bc3f18f030f" />

**Question 9**
---

<img width="1096" height="708" alt="image" src="https://github.com/user-attachments/assets/fc7851c6-3cc8-4fbb-a5be-a16f481984fe" />


```sql
SELECT 
    ename,
    hiredate,
    CASE strftime('%w', hiredate)
        WHEN '0' THEN 'Sunday'
        WHEN '1' THEN 'Monday'
        WHEN '2' THEN 'Tuesday'
        WHEN '3' THEN 'Wednesday'
        WHEN '4' THEN 'Thursday'
        WHEN '5' THEN 'Friday'
        WHEN '6' THEN 'Saturday'
    END AS day_of_week
FROM emp;
```

**Output:**

<img width="1236" height="421" alt="image" src="https://github.com/user-attachments/assets/28002d88-1a2d-4f03-ad37-48d7458c22b8" />


**Question 10**
---

<img width="1223" height="494" alt="image" src="https://github.com/user-attachments/assets/106571ce-cff6-434a-8986-61ea9757006a" />


```sql
DELETE FROM customer
WHERE GRADE % 2 <> 0;
```

**Output:**

<img width="1244" height="485" alt="image" src="https://github.com/user-attachments/assets/f42e9772-b1b1-4431-b532-bb55c4891595" />


## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
