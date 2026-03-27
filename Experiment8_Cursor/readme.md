# Experiment 8: PL/SQL Cursor Programs

## AIM
To write and execute PL/SQL programs using cursors and exception handling to manage runtime errors effectively and display appropriate messages.

## THEORY

In PL/SQL, cursors are used to handle query result sets row-by-row. 

There are two types of cursors:

- Implicit Cursors: Automatically created by PL/SQL for single-row queries.
- Explicit Cursors: Declared and controlled by the programmer for multi-row queries.

Types of Explicit Cursors:

1. Simple Cursor: Basic cursor to iterate over multiple rows.

2. Parameterized Cursor: Accepts parameters to filter the result dynamically.

3. Cursor FOR Loop: Simplifies cursor operations (open, fetch, close).

4. %ROWTYPE Cursor: Fetches entire row into a record using %ROWTYPE.

5. Cursor with FOR UPDATE: Used for row-level locking and updating the rows while looping.

**Syntax:**
```sql
DECLARE 
   <declarations section> 
BEGIN 
   <executable command(s)>
EXCEPTION 
   <exception handling> 
END;
```

### Basic Components of PL/SQL Block:

- DECLARE: Section to declare variables and constants.
- BEGIN: The execution section that contains PL/SQL statements.
- EXCEPTION: Handles errors or exceptions that occur in the program.
- END: Marks the end of the PL/SQL block.

**Exception Handling**

PL/SQL provides a robust mechanism to handle runtime errors using exception handling blocks. When an error occurs during execution, control is passed to the EXCEPTION section, where specific or general errors can be handled gracefully.

### Components of Exception Handling:
- Predefined Exceptions: Automatically raised by PL/SQL for common errors (e.g., NO_DATA_FOUND, TOO_MANY_ROWS, ZERO_DIVIDE).
- User-defined Exceptions: Declared explicitly in the declaration section using the EXCEPTION keyword.
- WHEN OTHERS: A generic handler for all exceptions not handled explicitly.

```sql
BEGIN
   -- Statements
EXCEPTION
   WHEN exception_name THEN
      -- Handling code
   WHEN OTHERS THEN
      -- Handling for unknown errors
END;
```

### **Question 1: Simple Cursor with Exception Handling**

**Write a PL/SQL program using a simple cursor to fetch employee names and designations from the `employees` table. Implement exception handling for the following cases:**

1. **NO_DATA_FOUND**: When no rows are fetched.
2. **OTHERS**: Any other unexpected errors during execution.

**Steps:**

- Create an `employees` table with fields `emp_id`, `emp_name`, and `designation`.
- Insert some sample data into the table.
- Use a simple cursor to fetch and display employee names and designations.
- Implement exception handling to catch the relevant exceptions and display appropriate messages.

#### PL/SQL Query - 1

``` SQL
BEGIN
    EXECUTE IMMEDIATE 'DROP TABLE employees';
EXCEPTION
    WHEN OTHERS THEN
        NULL; -
END;
/

CREATE TABLE employees (
    emp_id       NUMBER PRIMARY KEY,
    emp_name     VARCHAR2(100),
    designation  VARCHAR2(100)
);

BEGIN
    INSERT INTO employees VALUES (1, 'Alice', 'Manager');
    INSERT INTO employees VALUES (2, 'Bob', 'Developer');
    INSERT INTO employees VALUES (3, 'Charlie', 'Analyst');
    COMMIT;
END;
/

DECLARE
    CURSOR emp_cursor IS
        SELECT emp_name, designation FROM employees;

    v_emp_name     employees.emp_name%TYPE;
    v_designation  employees.designation%TYPE;

    v_found        BOOLEAN := FALSE;

BEGIN
    OPEN emp_cursor;

    LOOP
        FETCH emp_cursor INTO v_emp_name, v_designation;
        EXIT WHEN emp_cursor%NOTFOUND;

        v_found := TRUE;

        DBMS_OUTPUT.PUT_LINE('Name: ' || v_emp_name || ', Designation: ' || v_designation);
    END LOOP;

    CLOSE emp_cursor;

    IF NOT v_found THEN
        RAISE NO_DATA_FOUND;
    END IF;

EXCEPTION
    WHEN NO_DATA_FOUND THEN
        DBMS_OUTPUT.PUT_LINE('No employee records found.');
    WHEN OTHERS THEN
        DBMS_OUTPUT.PUT_LINE('An unexpected error occurred: ' || SQLERRM);
END;
/
```
#### PL/SQL Query - 2

``` SQL
SET SERVEROUTPUT ON;

BEGIN
    EXECUTE IMMEDIATE 'DROP TABLE employees';
EXCEPTION
    WHEN OTHERS THEN
        NULL; 
END;


CREATE TABLE employees (
    emp_id      NUMBER PRIMARY KEY,
    emp_name    VARCHAR2(100),
    designation VARCHAR2(100)
);

DECLARE
    CURSOR emp_cursor IS
        SELECT emp_name, designation FROM employees;

    v_emp_name employees.emp_name%TYPE;
    v_designation employees.designation%TYPE;
    v_found BOOLEAN := FALSE;

BEGIN
    OPEN emp_cursor;
    LOOP
        FETCH emp_cursor INTO v_emp_name, v_designation;
        EXIT WHEN emp_cursor%NOTFOUND;

        v_found := TRUE;
        DBMS_OUTPUT.PUT_LINE('Name: ' || v_emp_name || ', Designation: ' || v_designation);
    END LOOP;
    CLOSE emp_cursor;

    IF NOT v_found THEN
        RAISE_APPLICATION_ERROR(-20001, 'No employee records found.');
    END IF;

EXCEPTION
    WHEN OTHERS THEN
        DBMS_OUTPUT.PUT_LINE(SQLERRM);
END;
/
```
### Expected Output:  
The program should display the employee details or an error message.

### Output Got:

#### 1.

<img width="340" height="82" alt="image" src="https://github.com/user-attachments/assets/d185fbb3-bfa5-4906-81d3-3a7cd027809c" />


#### 2.

<img width="352" height="97" alt="image" src="https://github.com/user-attachments/assets/d407b75b-5939-4b06-a2a4-a1cd2c784e4d" />

---


### **Question 2: Parameterized Cursor with Exception Handling**

**Write a PL/SQL program using a parameterized cursor to retrieve and display employees with a salary in a given range. Implement exception handling for the following errors:**

1. **NO_DATA_FOUND**: When no employees meet the salary criteria.
2. **OTHERS**: For any unexpected errors during the execution.

**Steps:**

- Modify the `employees` table by adding a `salary` column.
- Insert sample salary values for the employees.
- Use a parameterized cursor to accept a salary range as input and fetch employees within that range.
- Implement exception handling to catch and display relevant error messages.

#### PL/SQL QUERY - 1

``` SQL
BEGIN
    EXECUTE IMMEDIATE 'DROP TABLE employees';
EXCEPTION
    WHEN OTHERS THEN
        NULL; 
END;
/

CREATE TABLE employees (
    emp_id       NUMBER PRIMARY KEY,
    emp_name     VARCHAR2(100),
    designation  VARCHAR2(100),
    salary       NUMBER
);

BEGIN
    INSERT INTO employees VALUES (1, 'Alice', 'Manager', 6000);
    INSERT INTO employees VALUES (2, 'Bob', 'Developer', 4000);
    INSERT INTO employees VALUES (3, 'Charlie', 'Analyst', 3500);
    INSERT INTO employees VALUES (4, 'David', 'Tester', 3000);
    INSERT INTO employees VALUES (5, 'Eve', 'Designer', 4500);
    COMMIT;
END;
/

DECLARE
    v_min_salary NUMBER := 3500;
    v_max_salary NUMBER := 5000;

    CURSOR emp_cursor(p_min NUMBER, p_max NUMBER) IS
        SELECT emp_name, designation, salary
        FROM employees
        WHERE salary BETWEEN p_min AND p_max;

    v_name        employees.emp_name%TYPE;
    v_designation employees.designation%TYPE;
    v_salary      employees.salary%TYPE;

    v_found       BOOLEAN := FALSE;

BEGIN
    OPEN emp_cursor(v_min_salary, v_max_salary);

    LOOP
        FETCH emp_cursor INTO v_name, v_designation, v_salary;
        EXIT WHEN emp_cursor%NOTFOUND;

        v_found := TRUE;
        DBMS_OUTPUT.PUT_LINE('Name: ' || v_name || 
                             ', Designation: ' || v_designation ||
                             ', Salary: ' || v_salary);
    END LOOP;

    CLOSE emp_cursor;

    IF NOT v_found THEN
        RAISE NO_DATA_FOUND;
    END IF;

EXCEPTION
    WHEN NO_DATA_FOUND THEN
        DBMS_OUTPUT.PUT_LINE('No employees found in the salary range ' || 
                             v_min_salary || ' to ' || v_max_salary || '.');
    WHEN OTHERS THEN
        DBMS_OUTPUT.PUT_LINE('An unexpected error occurred: ' || SQLERRM);
END;
/
```

#### PL/SQL QUERY - 2

``` SQL
SET SERVEROUTPUT ON;
/

BEGIN
    EXECUTE IMMEDIATE 'DROP TABLE employees';
EXCEPTION
    WHEN OTHERS THEN
        NULL; 
END;
/

CREATE TABLE employees (
    emp_id       NUMBER PRIMARY KEY,
    emp_name     VARCHAR2(100),
    designation  VARCHAR2(100),
    salary       NUMBER
);
/


BEGIN
    INSERT INTO employees VALUES (1, 'Alice', 'Manager', 8000);
    INSERT INTO employees VALUES (2, 'Bob', 'Developer', 4500);
    INSERT INTO employees VALUES (3, 'Charlie', 'Analyst', 5000);
    INSERT INTO employees VALUES (4, 'David', 'Tester', 3000);
    INSERT INTO employees VALUES (5, 'Eve', 'Designer', 6500);
    COMMIT;
END;
/

DECLARE
    v_min_salary NUMBER := 9000;
    v_max_salary NUMBER := 10000;

    CURSOR emp_cursor(p_min NUMBER, p_max NUMBER) IS
        SELECT emp_id, emp_name, designation, salary
        FROM employees
        WHERE salary BETWEEN p_min AND p_max;

    v_found BOOLEAN := FALSE;

BEGIN
    FOR emp_rec IN emp_cursor(v_min_salary, v_max_salary) LOOP
        v_found := TRUE;
        DBMS_OUTPUT.PUT_LINE(
            'ID: ' || emp_rec.emp_id ||
            ', Name: ' || emp_rec.emp_name ||
            ', Designation: ' || emp_rec.designation ||
            ', Salary: ' || emp_rec.salary
        );
    END LOOP;

    IF NOT v_found THEN
        RAISE NO_DATA_FOUND;
    END IF;

EXCEPTION
    WHEN NO_DATA_FOUND THEN
        DBMS_OUTPUT.PUT_LINE('No employees found in the specified salary range.');
    WHEN OTHERS THEN
        DBMS_OUTPUT.PUT_LINE('An unexpected error occurred: ' || SQLERRM);
END;
/
```

### Expected Output:  
The program should display the employee details within the specified salary range or an error message if no data is found.

### Output Got:

#### 1.

<img width="357" height="59" alt="image" src="https://github.com/user-attachments/assets/791e624c-dab4-4b6c-9dc4-81764f8c3033" />


#### 2.

<img width="407" height="89" alt="image" src="https://github.com/user-attachments/assets/de73cf75-69a2-4f7b-8e93-e73a8db62e8c" />

---

### **Question 3: Cursor FOR Loop with Exception Handling**

**Write a PL/SQL program using a cursor FOR loop to retrieve and display all employee names and their department numbers from the `employees` table. Implement exception handling for the following cases:**

1. **NO_DATA_FOUND**: If no employees are found in the database.
2. **OTHERS**: For any other unexpected errors.

**Steps:**

- Modify the `employees` table by adding a `dept_no` column.
- Insert sample department numbers for employees.
- Use a cursor FOR loop to fetch and display employee names along with their department numbers.
- Implement exception handling to catch the relevant exceptions.

#### PL/SQL QUERY - 1

``` SQL
BEGIN
    EXECUTE IMMEDIATE 'DROP TABLE employees';
EXCEPTION
    WHEN OTHERS THEN
        NULL; 
END;
/

CREATE TABLE employees (
    emp_id     NUMBER PRIMARY KEY,
    emp_name   VARCHAR2(100),
    designation VARCHAR2(100),
    salary     NUMBER,
    dept_no    NUMBER
);

BEGIN
    INSERT INTO employees VALUES (1, 'Alice', 'Manager', 6000, 10);
    INSERT INTO employees VALUES (2, 'Bob', 'Developer', 4000, 20);
    INSERT INTO employees VALUES (3, 'Charlie', 'Analyst', 3500, 10);
    INSERT INTO employees VALUES (4, 'David', 'Tester', 3000, 30);
    INSERT INTO employees VALUES (5, 'Eve', 'Designer', 4500, 20);
    COMMIT;
END;
/

DECLARE
    v_found BOOLEAN := FALSE;

BEGIN
    FOR emp_rec IN (
        SELECT emp_name, dept_no FROM employees
    ) LOOP
        v_found := TRUE;
        DBMS_OUTPUT.PUT_LINE('Name: ' || emp_rec.emp_name || 
                             ', Department No: ' || emp_rec.dept_no);
    END LOOP;

    IF NOT v_found THEN
        RAISE NO_DATA_FOUND;
    END IF;

EXCEPTION
    WHEN NO_DATA_FOUND THEN
        DBMS_OUTPUT.PUT_LINE('No employee records found.');
    WHEN OTHERS THEN
        DBMS_OUTPUT.PUT_LINE('An unexpected error occurred: ' || SQLERRM);
END;
/
```

#### PL/SQL QUERY - 2

``` SQL
SET SERVEROUTPUT ON;
/

BEGIN
    EXECUTE IMMEDIATE 'DROP TABLE employees';
EXCEPTION
    WHEN OTHERS THEN
        NULL; 
END;
/

CREATE TABLE employees (
    emp_id      NUMBER PRIMARY KEY,
    emp_name    VARCHAR2(100),
    designation VARCHAR2(100),
    salary      NUMBER,
    dept_no     NUMBER
);
/


DECLARE
    v_found BOOLEAN := FALSE;
BEGIN
    FOR emp_rec IN (
        SELECT emp_name, dept_no FROM employees
    ) LOOP
        v_found := TRUE;
        DBMS_OUTPUT.PUT_LINE('Name: ' || emp_rec.emp_name || 
                             ', Department No: ' || emp_rec.dept_no);
    END LOOP;

    -- Check if no data was found
    IF NOT v_found THEN
        RAISE NO_DATA_FOUND;
    END IF;

EXCEPTION
    WHEN NO_DATA_FOUND THEN
        DBMS_OUTPUT.PUT_LINE('No employee records found.');
    WHEN OTHERS THEN
        DBMS_OUTPUT.PUT_LINE('An unexpected error occurred: ' || SQLERRM);
END;
/
```

### Expected Output:
The program should display employee names with their department numbers or the appropriate error message if no data is found.

### Output Got:

#### 1.

<img width="358" height="67" alt="image" src="https://github.com/user-attachments/assets/aa3b17ee-cac6-451a-a960-280a7f5d1cd7" />


#### 2.

<img width="385" height="95" alt="image" src="https://github.com/user-attachments/assets/9542e414-1ff0-46e9-b6a2-25b62b3a8244" />


---

### **Question 4: Cursor with `%ROWTYPE` and Exception Handling**

**Write a PL/SQL program that uses a cursor with `%ROWTYPE` to fetch and display complete employee records (emp_id, emp_name, designation, salary). Implement exception handling for the following errors:**

1. **NO_DATA_FOUND**: When no employees are found in the database.
2. **OTHERS**: For any other errors that occur.

**Steps:**

- Modify the `employees` table by adding `emp_id`, `emp_name`, `designation`, and `salary` fields.
- Insert sample data into the `employees` table.
- Declare a cursor using `%ROWTYPE` to fetch complete rows from the `employees` table.
- Implement exception handling to catch the relevant exceptions and display appropriate messages.

#### PL/SQL QUERY - 1

``` SQL
BEGIN
    EXECUTE IMMEDIATE 'DROP TABLE employees';
EXCEPTION
    WHEN OTHERS THEN
        NULL; 
END;
/

CREATE TABLE employees (
    emp_id       NUMBER PRIMARY KEY,
    emp_name     VARCHAR2(100),
    designation  VARCHAR2(100),
    salary       NUMBER
);

BEGIN
    INSERT INTO employees VALUES (1, 'Alice', 'Manager', 6000);
    INSERT INTO employees VALUES (2, 'Bob', 'Developer', 4000);
    INSERT INTO employees VALUES (3, 'Charlie', 'Analyst', 3500);
    INSERT INTO employees VALUES (4, 'David', 'Tester', 3000);
    INSERT INTO employees VALUES (5, 'Eve', 'Designer', 4500);
    COMMIT;
END;
/

DECLARE
    CURSOR emp_cursor IS
        SELECT * FROM employees;

    emp_record emp_cursor%ROWTYPE;
    v_found    BOOLEAN := FALSE;

BEGIN
    OPEN emp_cursor;

    LOOP
        FETCH emp_cursor INTO emp_record;
        EXIT WHEN emp_cursor%NOTFOUND;

        v_found := TRUE;

        DBMS_OUTPUT.PUT_LINE('ID: ' || emp_record.emp_id ||
                             ', Name: ' || emp_record.emp_name ||
                             ', Designation: ' || emp_record.designation ||
                             ', Salary: ' || emp_record.salary);
    END LOOP;

    CLOSE emp_cursor;

    IF NOT v_found THEN
        RAISE NO_DATA_FOUND;
    END IF;

EXCEPTION
    WHEN NO_DATA_FOUND THEN
        DBMS_OUTPUT.PUT_LINE('No employee records found.');
    WHEN OTHERS THEN
        DBMS_OUTPUT.PUT_LINE('An unexpected error occurred: ' || SQLERRM);
END;
/
```

#### PL/SQL QUERY - 2

``` SQL
SET SERVEROUTPUT ON;

BEGIN
  EXECUTE IMMEDIATE 'DROP TABLE employees';
EXCEPTION
  WHEN OTHERS THEN
    NULL;  
END;


CREATE TABLE employees (
  emp_id      NUMBER PRIMARY KEY,
  emp_name    VARCHAR2(100),
  designation VARCHAR2(100),
  salary      NUMBER
);

BEGIN
  INSERT INTO employees VALUES (1, 'Alice', 'Manager', 6000);
  COMMIT;
END;
/

DECLARE
  CURSOR c_emp IS
    SELECT * FROM employees;
  v_emp   c_emp%ROWTYPE;
  v_dummy NUMBER;
BEGIN
  OPEN c_emp;
    FETCH c_emp INTO v_emp;
  CLOSE c_emp;

  v_dummy := v_emp.salary / 0;

EXCEPTION
  WHEN NO_DATA_FOUND THEN
    DBMS_OUTPUT.PUT_LINE('No employee records found.');
  WHEN OTHERS THEN
    DBMS_OUTPUT.PUT_LINE('An unexpected error occurred.');
END;
/
```

### Expected Output:  
The program should display employee records or the appropriate error message if no data is found.

### Output Got:

#### 1.

<img width="488" height="199" alt="image" src="https://github.com/user-attachments/assets/efa5b0e7-8a39-454b-bc6b-5ecadbb054ad" />


#### 2.

<img width="400" height="98" alt="image" src="https://github.com/user-attachments/assets/65ce7373-d278-4368-9e76-fa1cd96d7746" />

---

### **Question 5: Cursor with FOR UPDATE Clause and Exception Handling**

**Write a PL/SQL program using a cursor with the `FOR UPDATE` clause to update the salary of employees in a specific department. Implement exception handling for the following cases:**

1. **NO_DATA_FOUND**: If no rows are affected by the update.
2. **OTHERS**: For any unexpected errors during execution.

**Steps:**

- Modify the `employees` table to include a `dept_no` and `salary` field.
- Insert sample data into the `employees` table with different department numbers.
- Use a cursor with the `FOR UPDATE` clause to lock the rows of employees in a specific department and update their salary.
- Implement exception handling to handle `NO_DATA_FOUND` or other errors that may occur.

#### PL/SQL QUERY

``` SQL
BEGIN
    EXECUTE IMMEDIATE 'DROP TABLE employees';
EXCEPTION
    WHEN OTHERS THEN
        NULL; 
END;
/
CREATE TABLE employees (
    emp_id   NUMBER PRIMARY KEY,
    emp_name VARCHAR2(100),
    dept_no  NUMBER,
    salary   NUMBER
);
BEGIN
    INSERT INTO employees VALUES (1, 'Alice', 10, 3000);
    INSERT INTO employees VALUES (2, 'Bob', 20, 4000);
    INSERT INTO employees VALUES (3, 'Charlie', 10, 3500);
    INSERT INTO employees VALUES (4, 'David', 30, 4500);
    INSERT INTO employees VALUES (5, 'Eve', 20, 3200);
    COMMIT;
END;
/
DECLARE
    CURSOR emp_cursor IS
        SELECT emp_id, salary
        FROM employees
        WHERE dept_no = 10
        FOR UPDATE;

    v_emp_id   employees.emp_id%TYPE;
    v_salary   employees.salary%TYPE;

    v_found    BOOLEAN := FALSE;

BEGIN
    OPEN emp_cursor;

    LOOP
        FETCH emp_cursor INTO v_emp_id, v_salary;
        EXIT WHEN emp_cursor%NOTFOUND;

        v_found := TRUE;
        UPDATE employees
        SET salary = v_salary * 1.10
        WHERE emp_id = v_emp_id;
    END LOOP;
    CLOSE emp_cursor;
    IF v_found THEN
        DBMS_OUTPUT.PUT_LINE('Salaries updated for department 10.');
    ELSE
        RAISE NO_DATA_FOUND;
    END IF;
EXCEPTION
    WHEN NO_DATA_FOUND THEN
        DBMS_OUTPUT.PUT_LINE('No employees found in the specified department.');
    WHEN OTHERS THEN
        DBMS_OUTPUT.PUT_LINE('An unexpected error occurred: ' || SQLERRM);
END;
/
```


### Expected Output:  
The program should update employee salaries and display a message, or it should display an error message if no data is found.

### Output Got:

<img width="336" height="92" alt="image" src="https://github.com/user-attachments/assets/cc444628-e12f-4cf6-a72f-614cc8bfda61" />

---

## RESULT
Thus, the program successfully executed and displayed employee details using a cursor. 
****
