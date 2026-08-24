# Experiment 7: PL/SQL – Variables, Control Structures and Loops
## Name : HARI PRASATH E 
## Reg No : 212225040107
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

## 1. Write a PL/SQL program to find the Greatest of Two Numbers

### Steps:
- Declare two numeric variables and initialize them.
- Use an `IF` statement to compare the values.
- Display the greater number using `DBMS_OUTPUT.PUT_LINE`.

### CODE 
```
DECLARE
   a NUMBER := 45;
   b NUMBER := 80;
BEGIN
   IF a > b THEN
      DBMS_OUTPUT.PUT_LINE('Greater number is: ' || a);
   ELSE
      DBMS_OUTPUT.PUT_LINE('Greater number is: ' || b);
   END IF;
END;
/
```

## Expected Output: 
### Greater number is: 80
<img width="706" height="771" alt="image" src="https://github.com/user-attachments/assets/bf7b46de-365e-4220-b066-628420b38902" />

---

## 2. Write a PL/SQL program to Calculate Sum of First N Natural Numbers

### Steps:
- Declare a variable `n` and assign a value (e.g., 10).
- Initialize a `sum` variable to 0.
- Use a `WHILE` loop to iterate from 1 to `n`, adding each number to the sum.
- Display the result using `DBMS_OUTPUT.PUT_LINE`.

## CODE
```
DECLARE
   n NUMBER := 10;
   i NUMBER := 1;
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

## Expected Output:
### Sum of first 10 natural numbers is: 55
<img width="832" height="788" alt="image" src="https://github.com/user-attachments/assets/a7082d30-aa5d-46cd-a8be-e62ff02b882e" />

---

## 3. Write a PL/SQL program to generate Fibonacci series

### Steps:
- Declare the variable `n` to indicate how many terms to generate.
- Initialize the first two Fibonacci numbers (0 and 1).
- Use a loop to generate the next terms using the formula `c = a + b`.
- Print each term in the series.

## CODE
```
DECLARE
   n NUMBER := 7;
   a NUMBER := 0;
   b NUMBER := 1;
   c NUMBER;
   i NUMBER;
   fib VARCHAR2(200) := '0, 1';
BEGIN
   DBMS_OUTPUT.PUT_LINE('n = ' || n);
   FOR i IN 3..n LOOP
      c := a + b;
      fib := fib || ', ' || c;
      a := b;
      b := c;
   END LOOP;
   DBMS_OUTPUT.PUT_LINE('Fibonacci sequence: ' || fib);
END;
/
```
## Expected Output:
### n = 7  
### Fibonacci sequence: 0, 1, 1, 2, 3, 5, 8
<img width="734" height="770" alt="image" src="https://github.com/user-attachments/assets/8bef5ad0-1421-496c-8456-bde91f8bdf2d" />

---

## 4. Write a PL/SQL Program to display the number in Reverse Order

### Steps:
- Declare a variable `n` and assign a value (e.g., 1535).
- Use a loop to extract each digit using modulo and reverse the number.
- Display the reversed number.

## CODE
```
DECLARE
   n NUMBER := 1535;
   temp NUMBER := n;
   rev NUMBER := 0;
   digit NUMBER;
BEGIN
   WHILE temp > 0 LOOP
      digit := MOD(temp, 10);
      rev := (rev * 10) + digit;
      temp := TRUNC(temp / 10);
   END LOOP;
   DBMS_OUTPUT.PUT_LINE('n = ' || n);
   DBMS_OUTPUT.PUT_LINE('Reversed number is ' || rev);
END;
/
```
## Expected Output: 
### n = 1535  
### Reversed number is 5351
<img width="718" height="772" alt="image" src="https://github.com/user-attachments/assets/94842f30-9909-4fa0-b246-fccf890e2431" />

---

## 5. Write a PL/SQL program to find the largest of three numbers

### Steps:
- Declare three numeric variables `a`, `b`, and `c`.
- Use nested `IF-ELSIF-ELSE` conditions to find the largest among the three.
- Display the largest number.
## CODE
```
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
   DBMS_OUTPUT.PUT_LINE('a = ' || a || ', b = ' || b || ', c = ' || c);
   DBMS_OUTPUT.PUT_LINE('Largest of three number is ' || largest);
END;
/
```
## Expected Output:  
### a = 10, b = 9, c = 15  
### Largest of three number is 15
<img width="759" height="769" alt="image" src="https://github.com/user-attachments/assets/28c19ebb-251c-40e6-afc4-493cef1f9996" />

# RESULT
Thus, the PL/SQL programs using variables, conditionals, and loops were executed successfully.
