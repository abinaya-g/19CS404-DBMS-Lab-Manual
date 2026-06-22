# Experiment 2: DDL Commands

## AIM
To study and implement DDL commands and different types of constraints.

## THEORY

### 1. CREATE
Used to create a new relation (table).

**Syntax:**
```sql
CREATE TABLE (
  field_1 data_type(size),
  field_2 data_type(size),
  ...
);
```
### 2. ALTER
Used to add, modify, drop, or rename fields in an existing relation.
(a) ADD
```sql
ALTER TABLE std ADD (Address CHAR(10));
```
(b) MODIFY
```sql
ALTER TABLE relation_name MODIFY (field_1 new_data_type(size));
```
(c) DROP
```sql
ALTER TABLE relation_name DROP COLUMN field_name;
```
(d) RENAME
```sql
ALTER TABLE relation_name RENAME COLUMN old_field_name TO new_field_name;
```
### 3. DROP TABLE
Used to permanently delete the structure and data of a table.
```sql
DROP TABLE relation_name;
```
### 4. RENAME
Used to rename an existing database object.
```sql
RENAME TABLE old_relation_name TO new_relation_name;
```
### CONSTRAINTS
Constraints are used to specify rules for the data in a table. If there is any violation between the constraint and the data action, the action is aborted by the constraint. It can be specified when the table is created (using CREATE TABLE) or after it is created (using ALTER TABLE).
### 1. NOT NULL
When a column is defined as NOT NULL, it becomes mandatory to enter a value in that column.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) NOT NULL
);
```
### 2. UNIQUE
Ensures that values in a column are unique.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) UNIQUE
);
```
### 3. CHECK
Specifies a condition that each row must satisfy.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) CHECK (logical_expression)
);
```
### 4. PRIMARY KEY
Used to uniquely identify each record in a table.
Properties:
Must contain unique values.
Cannot be null.
Should contain minimal fields.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) PRIMARY KEY
);
```
### 5. FOREIGN KEY
Used to reference the primary key of another table.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size),
  FOREIGN KEY (column_name) REFERENCES other_table(column)
);
```
### 6. DEFAULT
Used to insert a default value into a column if no value is specified.

Syntax:
```sql
CREATE TABLE Table_Name (
  col_name1 data_type,
  col_name2 data_type,
  col_name3 data_type DEFAULT 'default_value'
);
```

**Question 1**
--

<img width="1166" height="546" alt="image" src="https://github.com/user-attachments/assets/b3bc8ad3-f1a1-4854-a710-fb4cf35d970a" />


```sql
SELECT *
FROM salesman
WHERE commission BETWEEN 0.12 AND 0.14;
```

**Output:**

<img width="1223" height="511" alt="image" src="https://github.com/user-attachments/assets/d4ed66b9-a8a8-4bbb-b34f-36564929edc0" />


**Question 2**
---

<img width="1215" height="522" alt="image" src="https://github.com/user-attachments/assets/311a1c18-30e7-4373-a2a4-8e617394cd0e" />


```sql
UPDATE products
SET reorder_lvl = 20
WHERE quantity < 10
  AND category = 'Snacks';
```

**Output:**


<img width="1222" height="539" alt="image" src="https://github.com/user-attachments/assets/edc6881b-4b79-47cb-92d0-1b26052889a5" />


**Question 3**
---

<img width="1097" height="329" alt="image" src="https://github.com/user-attachments/assets/da673a99-d96b-42cc-8920-3bd143f7f864" />


```sql
UPDATE products
SET sell_price = sell_price * 1.10
WHERE category = 'Bakery';
```

**Output:**


<img width="1256" height="654" alt="image" src="https://github.com/user-attachments/assets/c5164bcd-269e-460e-bb96-dd95242e951b" />


**Question 4**
---

<img width="1227" height="687" alt="image" src="https://github.com/user-attachments/assets/2cb0711d-2d40-4429-bad2-91e3e9e7592f" />


```sql
SELECT name, city
FROM salesman
WHERE city IN ('London', 'Rome');
```

**Output:**

<img width="701" height="433" alt="image" src="https://github.com/user-attachments/assets/a9eb2ff8-d89f-4a30-aa0f-27151ef31fe4" />


**Question 5**
---

<img width="985" height="807" alt="image" src="https://github.com/user-attachments/assets/98b27949-4cfe-4c18-8adc-93278ca7bf2b" />


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


<img width="1228" height="471" alt="image" src="https://github.com/user-attachments/assets/8cb93234-31ff-492e-a67a-afcbfc0b819e" />


**Question 6**
---

<img width="1210" height="610" alt="image" src="https://github.com/user-attachments/assets/6ce5ffda-139f-4f02-9307-49743c5db9f3" />


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


<img width="926" height="388" alt="image" src="https://github.com/user-attachments/assets/64469cad-b970-4b08-871c-08eee938165e" />


**Question 7**
---

<img width="1079" height="358" alt="image" src="https://github.com/user-attachments/assets/e75c155a-8e7f-4804-875b-d95619d3b950" />


```sql
UPDATE suppliers
SET supplier_name = 'A1 Suppliers'
WHERE supplier_id = 8;
```

**Output:**

<img width="1244" height="478" alt="image" src="https://github.com/user-attachments/assets/cb68f822-0b32-4803-bf3a-143c885628e7" />


**Question 8**
---

<img width="1194" height="532" alt="image" src="https://github.com/user-attachments/assets/26cba8ac-dcb3-4e83-892d-60ffca08741c" />


```sql
SELECT *
FROM salesman
WHERE name LIKE 'N__l%';
```

**Output:**


<img width="1244" height="371" alt="image" src="https://github.com/user-attachments/assets/69f52a0f-f7ee-424f-9450-f948c6943fb3" />

**Question 9**
---

<img width="1093" height="696" alt="image" src="https://github.com/user-attachments/assets/50b39a9f-970e-4da3-823f-5515830ff89e" />


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


<img width="926" height="473" alt="image" src="https://github.com/user-attachments/assets/f2d6610e-f382-4a9d-b007-f83ca5533aad" />


**Question 10**
---

<img width="1226" height="498" alt="image" src="https://github.com/user-attachments/assets/66e9ab6f-a94c-4eef-8d16-bd0a376dbec0" />


```sql
DELETE FROM customer
WHERE GRADE % 2 <> 0;
```

**Output:**


<img width="1265" height="487" alt="image" src="https://github.com/user-attachments/assets/1223c6e0-cf24-4c15-b29b-66cd9b14bb3a" />



## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
