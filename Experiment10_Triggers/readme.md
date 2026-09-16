# Experiment 10: PL/SQL – Triggers

## AIM
To write and execute PL/SQL trigger programs for automating actions in response to specific table events like INSERT, UPDATE, or DELETE.

---

## THEORY

A **trigger** is a stored PL/SQL block that is automatically executed or fired when a specified event occurs on a table or view. Triggers can be used for enforcing business rules, auditing changes, or automatic updates.

### Types of Triggers:
- **Before Trigger**: Executes before the operation (INSERT, UPDATE, DELETE).
- **After Trigger**: Executes after the operation.
- **Row-level Trigger**: Executes for each affected row.
- **Statement-level Trigger**: Executes once for the triggering statement.

**Basic Syntax:**
```sql
CREATE OR REPLACE TRIGGER trigger_name
BEFORE|AFTER INSERT|UPDATE|DELETE ON table_name
[FOR EACH ROW]
BEGIN
   -- trigger logic
END;
```

## 1. Write a trigger to log every insertion into a table.
**Steps:**
- Create two tables: `employees` (for storing data) and `employee_log` (for logging the inserts).
- Write an **AFTER INSERT** trigger on the `employees` table to log the new data into the `employee_log` table.
```
CREATE TABLE employees (
    emp_id NUMBER PRIMARY KEY,
    emp_name VARCHAR2(50),
    salary NUMBER
);

CREATE TABLE employee_log (
    log_id NUMBER GENERATED ALWAYS AS IDENTITY,
    emp_id NUMBER,
    emp_name VARCHAR2(50),
    salary NUMBER,
    log_date DATE
);
```
```
CREATE OR REPLACE TRIGGER trg_after_insert_emp
AFTER INSERT ON employees
FOR EACH ROW
BEGIN
    INSERT INTO employee_log (emp_id, emp_name, salary, log_date)
    VALUES (:NEW.emp_id, :NEW.emp_name, :NEW.salary, SYSDATE);
END;
/
```
```
INSERT INTO employees VALUES (101, 'Arun', 30000);
INSERT INTO employees VALUES (102, 'Bala', 35000);

COMMIT;
```
```
SELECT * FROM employee_log;
```
**Expected Output:**
- A new entry is added to the `employee_log` table each time a new record is inserted into the `employees` table.
<img width="1402" height="706" alt="b1" src="https://github.com/user-attachments/assets/ce2c00c9-a150-44ba-aa31-410406852505" />


## 2. Write a trigger to prevent deletion of records from a sensitive table.
**Steps:**
- Write a **BEFORE DELETE** trigger on the `sensitive_data` table.
- Use `RAISE_APPLICATION_ERROR` to prevent deletion and issue a custom error message.

```
CREATE TABLE sensitive_data (
    id NUMBER PRIMARY KEY,
    data VARCHAR2(100)
);
```
```
INSERT INTO sensitive_data VALUES (1, 'Confidential Record 1');
INSERT INTO sensitive_data VALUES (2, 'Confidential Record 2');

COMMIT;
```
```
CREATE OR REPLACE TRIGGER trg_prevent_delete
BEFORE DELETE ON sensitive_data
FOR EACH ROW
BEGIN
    RAISE_APPLICATION_ERROR(-20001, 'Deletion is not allowed on sensitive_data table!');
END;
/
```
```
DELETE FROM sensitive_data WHERE id = 1;
```
**Expected Output:**
- If an attempt is made to delete a record from `sensitive_data`, an error message is raised, e.g., `ERROR: Deletion not allowed on this table.`
<img width="1398" height="752" alt="b2" src="https://github.com/user-attachments/assets/154802e7-4230-49f3-8a41-d714cb2d0a70" />

## 3. Write a trigger to automatically update a `last_modified` timestamp.
**Steps:**
- Add a `last_modified` column to the `products` table.
- Write a **BEFORE UPDATE** trigger on the `products` table to set the `last_modified` column to the current timestamp whenever an update occurs.
```
CREATE TABLE products (
    product_id NUMBER PRIMARY KEY,
    product_name VARCHAR2(50),
    price NUMBER,
    last_modified TIMESTAMP
);
```
```
INSERT INTO products VALUES (1, 'Laptop', 50000, NULL);
INSERT INTO products VALUES (2, 'Mobile', 20000, NULL);

COMMIT;
```
```
CREATE OR REPLACE TRIGGER trg_update_last_modified
BEFORE UPDATE ON products
FOR EACH ROW
BEGIN
    :NEW.last_modified := SYSTIMESTAMP;
END;
/
```
```
UPDATE products
SET price = 55000
WHERE product_id = 1;
```

```
SELECT * FROM products;
```
**Expected Output:**
- The `last_modified` column in the `products` table is updated automatically to the current date and time when any record is updated.
<img width="1407" height="725" alt="B3" src="https://github.com/user-attachments/assets/c9c2c187-43fd-4960-910d-8fb0943e4e14" />


## 4. Write a trigger to keep track of the number of updates made to a table.
**Steps:**
- Create an `audit_log` table with a counter column.
- Write an **AFTER UPDATE** trigger on the `customer_orders` table to increment the counter in the `audit_log` table every time a record is updated.
```
-- Main table
CREATE TABLE customer_orders (
    order_id NUMBER PRIMARY KEY,
    customer_name VARCHAR2(50),
    amount NUMBER
);

-- Audit table (counter)
CREATE TABLE audit_log (
    update_count NUMBER
);
```
```
INSERT INTO audit_log VALUES (0);
COMMIT;
```
```
INSERT INTO customer_orders VALUES (1, 'Ravi', 1000);
INSERT INTO customer_orders VALUES (2, 'Priya', 2000);

COMMIT;
```
```
CREATE OR REPLACE TRIGGER trg_count_updates
AFTER UPDATE ON customer_orders
FOR EACH ROW
BEGIN
    UPDATE audit_log
    SET update_count = update_count + 1;
END;
/
```
```
UPDATE customer_orders SET amount = 1500 WHERE order_id = 1;
UPDATE customer_orders SET amount = 2500 WHERE order_id = 2;
```
```
SELECT * FROM audit_log;
```
**Expected Output:**
- The `audit_log` table will maintain a count of how many updates have been made to the `customer_orders` table.

<img width="1403" height="675" alt="B4" src="https://github.com/user-attachments/assets/ba048058-16ab-484c-bc41-8bf26e4a7d9e" />


## 5. Write a trigger that checks a condition before allowing insertion into a table.
**Steps:**
- Write a **BEFORE INSERT** trigger on the `employees` table to check if the inserted salary meets a specific condition (e.g., salary must be greater than 3000).
- If the condition is not met, raise an error to prevent the insert.
### PROGRAM
```
CREATE TABLE employees (
    emp_id NUMBER PRIMARY KEY,
    emp_name VARCHAR2(50),
    salary NUMBER
);
```
```
CREATE OR REPLACE TRIGGER trg_check_salary
BEFORE INSERT ON employees
FOR EACH ROW
BEGIN
    IF :NEW.salary <= 3000 THEN
        RAISE_APPLICATION_ERROR(
            -20002,
            'Salary must be greater than 3000!'
        );
    END IF;
END;
/
```
```
INSERT INTO employees VALUES (1, 'Arun', 5000);
```
```
INSERT INTO employees VALUES (2, 'Bala', 2000);
```
**Expected Output:**
- If the inserted salary in the `employees` table is below the condition (e.g., salary < 3000), the insert operation is blocked, and an error message is raised, such as: `ERROR: Salary below minimum threshold.`
<img width="1411" height="757" alt="Screenshot 2026-03-23 115700" src="https://github.com/user-attachments/assets/142b339b-dbd4-4b50-8f12-e5b25d83c285" />

## RESULT
Thus, the PL/SQL trigger programs were written and executed successfully.
