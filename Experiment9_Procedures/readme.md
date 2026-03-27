# Experiment 9: PL/SQL – Procedures and Functions

## AIM
To understand and implement procedures and functions in PL/SQL for performing various operations such as calculations, decision-making, and looping.

---

## THEORY

PL/SQL (Procedural Language/SQL) extends SQL by adding procedural constructs like variables, conditions, loops, procedures, and functions. Procedures and functions are subprograms that help modularize the code and improve reusability.

### **Procedure**
A PL/SQL **procedure** is a subprogram that performs a specific action. It does not return a value directly but can return values using `OUT` parameters.

**Syntax:**
```sql
CREATE OR REPLACE PROCEDURE procedure_name (parameters)
IS
BEGIN
   -- statements
END;
```

To call the procedure

```sql
EXEC procedure_name(arguments);
```

### **Function**
A PL/SQL **function** is a subprogram that returns a single value using the RETURN keyword.

```sql
CREATE OR REPLACE FUNCTION function_name (parameters)
RETURN datatype
IS
BEGIN
   -- statements
   RETURN value;
END;
```

To call the function:

```sql
SELECT function_name(arguments) FROM DUAL;
```

Key Differences:

-A procedure does not return a value, whereas a function must return a value.
-Functions can be called from SQL queries, procedures cannot (in most cases).

## 1. Write a PL/SQL Procedure to Find the Square of a Number

### Steps:
- Create a procedure named `find_square`.
- Declare a parameter to accept a number.
- Inside the procedure, compute the square of the input number.
- Use `DBMS_OUTPUT.PUT_LINE` to display the result.
- Call the procedure with a number as input.

#### PL/SQL Query:
__Procedure__
``` SQL
CREATE OR REPLACE PROCEDURE FIND_SQUARE (num IN NUMBER) IS
    square NUMBER;
BEGIN
    square := num * num;
    DBMS_OUTPUT.PUT_LINE('Square of ' || num || ' is ' || square);
END;
```
__Calling the Procedure__
``` SQL 
BEGIN
    FIND_SQUARE(6);
END;
/
```

### Expected Output: 
Square of 6 is 36

### Output Got:
<img width="365" height="103" alt="image" src="https://github.com/user-attachments/assets/9627bb4c-61b0-4401-97f0-4946078fa731" />

---

## 2. Write a PL/SQL Function to Return the Factorial of a Number

### Steps:
- Create a function named `get_factorial`.
- Declare a parameter to accept a number.
- Use a loop to calculate the factorial.
- Return the result using the `RETURN` statement.
- Call the function using a `SELECT` statement or in an anonymous block.
#### PL/SQL Query:
__Procedure__
```SQL
CREATE OR REPLACE FUNCTION GET_FACTORIAL(n IN NUMBER)
RETURN NUMBER
IS
    result NUMBER := 1;
BEGIN
    IF n < 0 THEN
        RAISE_APPLICATION_ERROR(-20001, 'Input must be a non-negative number');
    END IF;

    FOR i IN 1..n LOOP
        result := result * i;
    END LOOP;

    RETURN result;
END;

```
__Calling the Procedure__
```SQL
DECLARE
    num NUMBER := 5;
    fact NUMBER;
BEGIN
    fact := GET_FACTORIAL(num);
    DBMS_OUTPUT.PUT_LINE('Factorial of ' || num || ' is ' || fact);
END;
/
```


### Expected Output:
Factorial of 5 is 120

### Output Got:
<img width="384" height="95" alt="image" src="https://github.com/user-attachments/assets/423c4660-9996-41ba-b14b-baf92c9c0859" />

---

## 3. Write a PL/SQL Procedure to Check Whether a Number is Even or Odd

### Steps:
- Create a procedure named `check_even_odd`.
- Accept an input parameter.
- Use the `MOD` function to check if the number is divisible by 2.
- Display whether it is Even or Odd using `DBMS_OUTPUT.PUT_LINE`.

#### PL/SQL Query:
__Procedure__
``` SQL
CREATE OR REPLACE PROCEDURE check_even_odd(num IN NUMBER) IS
BEGIN
    IF MOD(num, 2) = 0 THEN
        DBMS_OUTPUT.PUT_LINE(num || ' is Even');
    ELSE
        DBMS_OUTPUT.PUT_LINE(num || ' is Odd');
    END IF;
END;
```
__Calling the procedure__
``` SQL
SET SERVEROUTPUT ON;
BEGIN
    check_even_odd(12);
END;
/
```

### Expected Output:  
12 is Even

### Output Got:
<img width="356" height="85" alt="image" src="https://github.com/user-attachments/assets/c613fe5d-dfb1-4ec3-9faa-8f0b1f014d3d" />

---

## 4. Write a PL/SQL Function to Return the Reverse of a Number

### Steps:
- Create a function named `reverse_number`.
- Accept an input number as parameter.
- Use a loop to reverse the digits of the number.
- Return the reversed number.
- Call the function and display the output.

#### PL/SQL Query:

__Procedure__
``` SQL
CREATE OR REPLACE FUNCTION reverse_number(n IN NUMBER)
RETURN NUMBER
IS
    rev NUMBER := 0;
    num NUMBER := n;
BEGIN
    WHILE num > 0 LOOP
        rev := (rev * 10) + MOD(num, 10);
        num := TRUNC(num / 10);
    END LOOP;

    RETURN rev;
END;

```
__Calling the Procedure__
``` SQL
SET SERVEROUTPUT ON;
DECLARE
    input_num NUMBER := 1234;
    reversed_num NUMBER;
BEGIN
    reversed_num := reverse_number(input_num);
    DBMS_OUTPUT.PUT_LINE('Reversed number of ' || input_num || ' is ' || reversed_num);
END;
/
```

### Expected Output:  
Reversed number of 1234 is 4321

### Output Got:
<img width="363" height="95" alt="image" src="https://github.com/user-attachments/assets/8dd02a19-561c-48a4-854f-c3758ef1a239" />

---

## 5. Write a PL/SQL Procedure to Display the Multiplication Table of a Number

### Steps:
- Create a procedure named `print_table`.
- Accept an input number.
- Use a loop from 1 to 10 to multiply the input number.
- Display the multiplication results using `DBMS_OUTPUT.PUT_LINE`.

#### PL/SQL Query:
__Procedure__
``` SQL
CREATE OR REPLACE PROCEDURE print_table(num IN NUMBER) IS
BEGIN
    DBMS_OUTPUT.PUT_LINE('Multiplication table of ' || num || ':');
    FOR i IN 1..10 LOOP
        DBMS_OUTPUT.PUT_LINE(num || ' x ' || i || ' = ' || (num * i));
    END LOOP;
END;

```
__Calling the procedure__
``` SQL
SET SERVEROUTPUT ON;
BEGIN
    print_table(5);
END;
/
```

### Expected Output:
Multiplication table of 5:  
5 x 1 = 5  
5 x 2 = 10  
5 x 3 = 15  
...  
5 x 10 = 50

### Output Got:
<img width="476" height="273" alt="image" src="https://github.com/user-attachments/assets/afe5ad08-04aa-4540-bcdd-7a821d100fa0" />

## RESULT
Thus, the PL/SQL programs using procedures and functions were written, compiled, and executed successfully.
