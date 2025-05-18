# Experiment 7: PL/SQL – Variables, Control Structures and Loops

## AIM
To write and execute simple PL/SQL programs using variables, loops, and conditional statements.


## THEORY

PL/SQL, which stands for Procedural Language extensions to the Structured Query Language (SQL). It is a combination of SQL along with the procedural features of programming languages.

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

# PL/SQL Programs – Steps and Expected Output
```
NAME: SHYAM S
REGISTER.NO: 212223240156
```
## 1. Write a PL/SQL program to find the Greatest of Two Numbers

### Steps:
- Declare two numeric variables and initialize them.
- Use an `IF` statement to compare the values.
- Display the greater number using `DBMS_OUTPUT.PUT_LINE`.

**Expected Output:**  
Greater number is: 80

**Code:**
```sql
DECLARE
   num1 NUMBER := 45;
   num2 NUMBER := 80;
BEGIN
   IF num1 > num2 THEN
      DBMS_OUTPUT.PUT_LINE('Greater number is: ' || num1);
   ELSE
      DBMS_OUTPUT.PUT_LINE('Greater number is: ' || num2);
   END IF;
END;
/
```

**Output:**  

![image](https://github.com/user-attachments/assets/6c87fae2-7aed-4dc5-8f46-afce76be0d58)

---

## 2. Write a PL/SQL program to Calculate Sum of First N Natural Numbers

### Steps:
- Declare a variable `n` and assign a value (e.g., 10).
- Initialize a `sum` variable to 0.
- Use a `WHILE` loop to iterate from 1 to `n`, adding each number to the sum.
- Display the result using `DBMS_OUTPUT.PUT_LINE`.

**Expected Output:**  
Sum of first 10 natural numbers is: 55

**Code:**
```sql
DECLARE
   n   NUMBER := 10;
   i   NUMBER := 1;
   sum NUMBER := 0;
BEGIN
   WHILE i <= n LOOP
      sum := sum + i;
      i := i + 1;
   END LOOP;

   DBMS_OUTPUT.PUT_LINE('Sum of first ' || n || ' natural numbers is: ' || sum);
END;
/

```

**Output:**

![image](https://github.com/user-attachments/assets/0a408c13-de7c-4b76-92cd-4fc4c09ce065)

---

## 3. Write a PL/SQL program to generate Fibonacci series

### Steps:
- Declare the variable `n` to indicate how many terms to generate.
- Initialize the first two Fibonacci numbers (0 and 1).
- Use a loop to generate the next terms using the formula `c = a + b`.
- Print each term in the series.

**Expected Output:**  
n = 7  
Fibonacci sequence: 0, 1, 1, 2, 3, 5, 8

**Code:**
```sql
DECLARE
   n   NUMBER := 7;
   a   NUMBER := 0;
   b   NUMBER := 1;
   c   NUMBER;
   i   NUMBER := 3;
BEGIN
   -- Print the first two terms
   DBMS_OUTPUT.PUT_LINE('Fibonacci sequence:');
   DBMS_OUTPUT.PUT(a || ', ');
   DBMS_OUTPUT.PUT(b);

   -- Loop to generate the next terms
   WHILE i <= n LOOP
      c := a + b;
      DBMS_OUTPUT.PUT(', ' || c);
      a := b;
      b := c;
      i := i + 1;
   END LOOP;
   DBMS_OUTPUT.NEW_LINE;
END;
/
```

**Output:**

![image](https://github.com/user-attachments/assets/41dec93a-1d2c-44c5-b8bd-156c26a5c388)

---

## 4. Write a PL/SQL Program to display the number in Reverse Order

### Steps:
- Declare a variable `n` and assign a value (e.g., 1535).
- Use a loop to extract each digit using modulo and reverse the number.
- Display the reversed number.

**Expected Output:**  
n = 1535  
Reversed number is 5351

**Code:**
```sql
DECLARE
   n         NUMBER := 1535;
   rev       NUMBER := 0;
   digit     NUMBER;
   original  NUMBER := 1535;
BEGIN
   WHILE n > 0 LOOP
      digit := MOD(n, 10);         -- Extract the last digit
      rev := rev * 10 + digit;     -- Build the reversed number
      n := TRUNC(n / 10);          -- Remove the last digit
   END LOOP;

   DBMS_OUTPUT.PUT_LINE('Reversed number is ' || rev);
END;
/

```

**Output:**

![image](https://github.com/user-attachments/assets/9d5896ad-ae89-4d71-aa64-a0f3f4659d80)

---

## 5. Write a PL/SQL program to find the largest of three numbers

### Steps:
- Declare three numeric variables `a`, `b`, and `c`.
- Use nested `IF-ELSIF-ELSE` conditions to find the largest among the three.
- Display the largest number.

**Expected Output:**  
a = 10, b = 9, c = 15  
Largest of three number is 15

**Code:**
```sql
DECLARE
   a NUMBER := 10;
   b NUMBER := 9;
   c NUMBER := 15;
   largest NUMBER;
BEGIN
   IF a >= b AND a >= c THEN
      largest := a;
   ELSIF b >= a AND b >= c THEN
      largest := b;
   ELSE
      largest := c;
   END IF;

   DBMS_OUTPUT.PUT_LINE('Largest of three number is ' || largest);
END;
/

```

**Output:**

![image](https://github.com/user-attachments/assets/11dcbe5f-2c2b-4e6d-879c-651267664111)

---
## RESULT
Thus, the PL/SQL programs using variables, conditionals, and loops were executed successfully.
