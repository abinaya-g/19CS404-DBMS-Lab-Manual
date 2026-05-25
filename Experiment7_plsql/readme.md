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

## 1. Write a PL/SQL program to find the Greatest of Two Numbers

### Steps:
- Declare two numeric variables and initialize them.
- Use an `IF` statement to compare the values.
- Display the greater number using `DBMS_OUTPUT.PUT_LINE`.

### Program:

```
DECLARE
   num1 NUMBER := 80;
   num2 NUMBER := 52;
BEGIN
   IF num1 > num2 THEN
      DBMS_OUTPUT.PUT_LINE('The greatest number is: ' || num1);
   ELSIF num2 > num1 THEN
      DBMS_OUTPUT.PUT_LINE('The greatest number is: ' || num2);
   ELSE
      DBMS_OUTPUT.PUT_LINE('Both numbers are equal.');
   END IF;
END;

```
**Expected Output:**  
Greater number is: 80

### Output:
<img width="903" height="177" alt="image" src="https://github.com/user-attachments/assets/12906be4-0a3b-46bb-a77f-94af628b4f24" />


## 2. Write a PL/SQL program to Calculate Sum of First N Natural Numbers

### Steps:
- Declare a variable `n` and assign a value (e.g., 10).
- Initialize a `sum` variable to 0.
- Use a `WHILE` loop to iterate from 1 to `n`, adding each number to the sum.
- Display the result using `DBMS_OUTPUT.PUT_LINE`.

### Program:

```
DECLARE
   n NUMBER := 10;
   i NUMBER := 1;
   sum_val NUMBER := 0;
BEGIN
   WHILE i <= n LOOP
      sum_val := sum_val + i;
      i := i + 1;
   END LOOP;


   DBMS_OUTPUT.PUT_LINE('The sum of the first ' || n || ' natural numbers is: ' || sum_val);
END;

```

**Expected Output:**  
Sum of first 10 natural numbers is: 55

---

### Output:

<img width="907" height="167" alt="image" src="https://github.com/user-attachments/assets/ae1f63c1-f172-4126-98ca-d737a88a2a3d" />


## 3. Write a PL/SQL program to generate Fibonacci series

### Steps:
- Declare the variable `n` to indicate how many terms to generate.
- Initialize the first two Fibonacci numbers (0 and 1).
- Use a loop to generate the next terms using the formula `c = a + b`.
- Print each term in the series.


### Program:

```
DECLARE
   n NUMBER := 7;          
   a NUMBER := 0;          
   b NUMBER := 1;          
   c NUMBER;               
   i NUMBER := 1;
   series VARCHAR2(100);   
BEGIN
   series := TO_CHAR(a) || ', ' || TO_CHAR(b);

   
   WHILE i <= n - 2 LOOP
      c := a + b;
      series := series || ', ' || TO_CHAR(c);
      a := b;
      b := c;
      i := i + 1;
   END LOOP;

   DBMS_OUTPUT.PUT_LINE('n = ' || n);
   DBMS_OUTPUT.PUT_LINE('Fibonacci sequence: ' || series);
END;

```
**Expected Output:**  
n = 7  
Fibonacci sequence: 0, 1, 1, 2, 3, 5, 8

---


### Output:

<img width="915" height="175" alt="image" src="https://github.com/user-attachments/assets/0c6459ff-64a3-4937-a350-98ec51d55503" />


## 4. Write a PL/SQL Program to display the number in Reverse Order

### Steps:
- Declare a variable `n` and assign a value (e.g., 1535).
- Use a loop to extract each digit using modulo and reverse the number.
- Display the reversed number.


### Program:

```
DECLARE
   n NUMBER := 1535;
   temp_n NUMBER;
   reversed_n NUMBER := 0;
   remainder NUMBER;
BEGIN
   temp_n := n;

   WHILE temp_n > 0 LOOP
      remainder := MOD(temp_n, 10);
      reversed_n := (reversed_n * 10) + remainder;
      temp_n := TRUNC(temp_n / 10);
   END LOOP;

   DBMS_OUTPUT.PUT_LINE('n = ' || n);
   DBMS_OUTPUT.PUT_LINE('Reversed number is ' || reversed_n);
END;

```
**Expected Output:**  
n = 1535  
Reversed number is 5351

---

### Output:
<img width="855" height="168" alt="image" src="https://github.com/user-attachments/assets/a116eb39-fd83-4c50-9a7a-0a14a2efaf1b" />


## 5. Write a PL/SQL program to find the largest of three numbers

### Steps:
- Declare three numeric variables `a`, `b`, and `c`.
- Use nested `IF-ELSIF-ELSE` conditions to find the largest among the three.
- Display the largest number.

### Program:

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

```
**Expected Output:**  
a = 10, b = 9, c = 15  
Largest of three number is 15


### Output:
<img width="807" height="182" alt="image" src="https://github.com/user-attachments/assets/71ff8573-db2b-4126-ba17-5a28a414b637" />


### Result:
Thus, the PL/SQL programs using variables, conditionals, and loops were executed successfully.

## RESULT
Thus, the PL/SQL programs using variables, conditionals, and loops were executed successfully.
