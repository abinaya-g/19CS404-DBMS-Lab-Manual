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

**Expected Output:**  
Square of 6 is 36

### Code:
```
CREATE OR REPLACE PROCEDURE find_square(n IN NUMBER) IS
    result NUMBER;
BEGIN
    result := n * n;
    DBMS_OUTPUT.PUT_LINE('Square of ' || n || ' is ' || result);
END;
/

BEGIN
    find_square(6);
END;
/
```

### Output:
![image](https://github.com/user-attachments/assets/066bf1ed-948d-4d2a-824d-502eca8ed349)

---

## 2. Write a PL/SQL Function to Return the Factorial of a Number

### Steps:
- Create a function named `get_factorial`.
- Declare a parameter to accept a number.
- Use a loop to calculate the factorial.
- Return the result using the `RETURN` statement.
- Call the function using a `SELECT` statement or in an anonymous block.

**Expected Output:**  
Factorial of 5 is 120

### Code:
```
CREATE OR REPLACE FUNCTION get_factorial(n IN NUMBER)
RETURN NUMBER IS
    result NUMBER := 1;
    i      NUMBER;
BEGIN
    IF n < 0 THEN
        RETURN NULL; -- Factorial undefined for negative numbers
    END IF;

    FOR i IN 1..n LOOP
        result := result * i;
    END LOOP;

    RETURN result;
END;
/
SELECT get_factorial(5) AS factorial FROM dual;
```

### Output:
![image](https://github.com/user-attachments/assets/e7e5f7db-49a2-4b18-9316-4c1b36368300)

---

## 3. Write a PL/SQL Procedure to Check Whether a Number is Even or Odd

### Steps:
- Create a procedure named `check_even_odd`.
- Accept an input parameter.
- Use the `MOD` function to check if the number is divisible by 2.
- Display whether it is Even or Odd using `DBMS_OUTPUT.PUT_LINE`.

**Expected Output:**  
12 is Even

### Code:
```
CREATE OR REPLACE PROCEDURE check_even_odd(n IN NUMBER) IS
BEGIN
    IF MOD(n, 2) = 0 THEN
        DBMS_OUTPUT.PUT_LINE(n || ' is Even');
    ELSE
        DBMS_OUTPUT.PUT_LINE(n || ' is Odd');
    END IF;
END;
/

BEGIN
    check_even_odd(12);
END;
/
```

### Output:
![image](https://github.com/user-attachments/assets/66584c8a-ef36-441b-a9aa-54732e10aed6)

---

## 4. Write a PL/SQL Function to Return the Reverse of a Number

### Steps:
- Create a function named `reverse_number`.
- Accept an input number as parameter.
- Use a loop to reverse the digits of the number.
- Return the reversed number.
- Call the function and display the output.

**Expected Output:**  
Reversed number of 1234 is 4321

### Code:
```
CREATE OR REPLACE FUNCTION reverse_number(n IN NUMBER)
RETURN NUMBER IS
    reversed NUMBER := 0;
    temp NUMBER := n;
    digit NUMBER;
BEGIN
    WHILE temp > 0 LOOP
        digit := MOD(temp, 10);
        reversed := (reversed * 10) + digit;
        temp := TRUNC(temp / 10);
    END LOOP;

    RETURN reversed;
END;
/
```

### Output:
![image](https://github.com/user-attachments/assets/b8dcc6f9-2e71-409d-aa60-9603acbae7f8)
---

## 5. Write a PL/SQL Procedure to Display the Multiplication Table of a Number

### Steps:
- Create a procedure named `print_table`.
- Accept an input number.
- Use a loop from 1 to 10 to multiply the input number.
- Display the multiplication results using `DBMS_OUTPUT.PUT_LINE`.

**Expected Output:**  
Multiplication table of 5:  
5 x 1 = 5  
5 x 2 = 10  
5 x 3 = 15  
...  
5 x 10 = 50

### Code:
```
CREATE OR REPLACE PROCEDURE print_table(n IN NUMBER) IS
BEGIN
    DBMS_OUTPUT.PUT_LINE('Multiplication table of ' || n || ':');
    FOR i IN 1..10 LOOP
        DBMS_OUTPUT.PUT_LINE(n || ' x ' || i || ' = ' || (n * i));
    END LOOP;
END;
/

BEGIN
    print_table(5);
END;
/
```

### Output:
![image](https://github.com/user-attachments/assets/e7844d26-c8b5-4ea6-a68f-f3c74116c80e)

## RESULT
Thus, the PL/SQL programs using procedures and functions were written, compiled, and executed successfully.
