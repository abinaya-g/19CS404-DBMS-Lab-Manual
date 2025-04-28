# Experiment 3: DML Commands

## AIM
To study and implement DML (Data Manipulation Language) commands.

## THEORY

### 1. INSERT INTO
Used to add records into a relation.
These are three type of INSERT INTO queries which are as
A)Inserting a single record
*Syntax (Single Row):*
sql
INSERT INTO table_name (field_1, field_2, ...) VALUES (value_1, value_2, ...);

*Syntax (Multiple Rows):*
sql
INSERT INTO table_name (field_1, field_2, ...) VALUES
(value_1, value_2, ...),
(value_3, value_4, ...);

*Syntax (Insert from another table):*
sql
INSERT INTO table_name SELECT * FROM other_table WHERE condition;

### 2. UPDATE
Used to modify records in a relation.
Syntax:
sql
UPDATE table_name SET column1 = value1, column2 = value2 WHERE condition;

### 3. DELETE
Used to delete records from a relation.
*Syntax (All rows):*
sql
DELETE FROM table_name;

*Syntax (Specific condition):*
sql
DELETE FROM table_name WHERE condition;

### 4. SELECT
Used to retrieve records from a table.
*Syntax:*
sql
SELECT column1, column2 FROM table_name WHERE condition;

*Question 1*
--
-- Write a SQL statement to Increase the selling price by 15% in the products table where quantity in stock is less than 50 and supplier ID is 10.

Products Table 

name          type       
----------    ---------- 
product_id     INT PRIMARY KEY        
product_name   VARCHAR(10) 
category       VARCHAR(50) 
cost_price     DECIMAL(10) 
sell_price     DECIMAL(10) 
reorder_lv     INT        
quantity       INT        
supplier_id    INT          

sql
```
 UPDATE products
SET sell_price = sell_price * 1.15
WHERE quantity < 50 AND supplier_id = 10;
```

*Output:*
```
Test	
select changes();
changes()
----------
4
changes()
----------
4
SELECT*FROM Products WHERE supplier_id = 10;

**Expected**
product_id  product_name      category    cost_price  sell_price  reorder_lvl  quantity    supplier_id
----------  ----------------  ----------  ----------  ----------  -----------  ----------  -----------
6           Detergent Powder  Snacks      60          80          20           40          10
7           Surf Excel Deter  Snacks      85          100         10           40          10
8           Detergent Ariel   Items       85          100         10           40          10
product_id  product_name      category    cost_price  sell_price  reorder_lvl  quantity    supplier_id
----------  ----------------  ----------  ----------  ----------  -----------  ----------  -----------
6           Detergent Powder  Snacks      60          92          20           40          10
7           Surf Excel Deter  Snacks      85          115.0       10           40          10
8           Detergent Ariel   Items       85          115.0       10           40          10

**Got**
product_id  product_name      category    cost_price  sell_price  reorder_lvl  quantity    supplier_id
----------  ----------------  ----------  ----------  ----------  -----------  ----------  -----------
6           Detergent Powder  Snacks      60          80          20           40          10
7           Surf Excel Deter  Snacks      85          100         10           40          10
8           Detergent Ariel   Items       85          100         10           40          10
product_id  product_name      category    cost_price  sell_price  reorder_lvl  quantity    supplier_id
----------  ----------------  ----------  ----------  ----------  -----------  ----------  -----------
6           Detergent Powder  Snacks      60          92          20           40          10
7           Surf Excel Deter  Snacks      85          115.0       10           40          10
8           Detergent Ariel   Items       85          115.0       10           40          10
```
*Question 2*
---
-- Write a SQL statement to Increase the salary by 500 and email as 'updated' for employees with job ID 'SA_REP' and commission percentage greater than 0.15

Employees table

---------------
employee_id
first_name
last_name
email
phone_number
hire_date
job_id
salary
commission_pct
manager_id
department_id

sql
```
UPDATE employees
SET salary = salary + 500,
email = 'updated'
WHERE job_id = 'SA_REP' 
AND commission_pct > 0.15;
```

*Output:*
```
Test
SELECT EMPLOYEE_ID, FIRST_NAME, EMAIL, SALARY, JOB_ID FROM EMPLOYEES
WHERE job_id = 'SA_REP' AND EMAIL='updated' LIMIT 5;

**Expected**
EMPLOYEE_ID  FIRST_NAME  EMAIL       SALARY      JOB_ID
-----------  ----------  ----------  ----------  ----------
150          Peter       updated     10500       SA_REP
151          David       updated     10000       SA_REP
152          Peter       updated     9500        SA_REP
153          Christophe  updated     8500        SA_REP
154          Nanette     updated     8000        SA_REP
EMPLOYEE_ID  FIRST_NAME  EMAIL       SALARY      JOB_ID
-----------  ----------  ----------  ----------  ----------
150          Peter       updated     10500       SA_REP
151          David       updated     10000       SA_REP
152          Peter       updated     9500        SA_REP
153          Christophe  updated     8500        SA_REP
154          Nanette     updated     8000        SA_REP

**Got**
EMPLOYEE_ID  FIRST_NAME  EMAIL       SALARY      JOB_ID
-----------  ----------  ----------  ----------  ----------
155          Oliver      OTUVAULT    7000        SA_REP
163          Danielle    DGREENE     9500        SA_REP
164          Mattea      MMARVINS    7200        SA_REP
165          David       DLEE        6800        SA_REP
166          Sundar      SANDE       6400        SA_REP
EMPLOYEE_ID  FIRST_NAME  EMAIL       SALARY      JOB_ID
-----------  ----------  ----------  ----------  ----------
155          Oliver      OTUVAULT    7000        SA_REP
163          Danielle    DGREENE     9500        SA_REP
164          Mattea      MMARVINS    7200        SA_REP
165          David       DLEE        6800        SA_REP
166          Sundar      SANDE       6400        SA_REP
```
*Question 3*
---
-- Write a SQL statement to double the availability of the product with product_id 1.

products table

---------------
product_id
product_name
category_id
availability

sql
```
UPDATE products
SET availability = availability * 2
WHERE product_id = 1;
```

*Output:*
```
Test		
SELECT * FROM products
WHERE product_id = 1;

**Expected**
product_id  product_name  category_id  availability
----------  ------------  -----------  ------------
1           Pear          50           100

**Got**
product_id  product_name  category_id  availability
----------  ------------  -----------  ------------
1           Pear          50           100
```
*Question 4*
---
-- Write a SQL statement to increase the salary of employees under the department 40, 90 and 110 according to the company rules.

Salary will be increased by 25% for the department 40, 15% for department 90 and 10% for the department 110 and the rest of the departments will remain same.

Employees table

---------------
employee_id
first_name
last_name
email
phone_number
hire_date
job_id
salary
commission_pct
manager_id
department_id

sql
```
UPDATE employees
SET salary = CASE
    WHEN department_id = 40 THEN salary * 1.25  -- 25% increase for department 40
    WHEN department_id = 90 THEN salary * 1.15  -- 15% increase for department 90
    WHEN department_id = 110 THEN salary * 1.10  -- 10% increase for department 110
    ELSE salary  -- No change for other departments
END;
```


*Output:*
```
Test	Expected	Got	
SELECT EMPLOYEE_ID, FIRST_NAME, SALARY, PHONE_NUMBER, EMAIL, JOB_ID FROM EMPLOYEES LIMIT 10;

**Expected**
EMPLOYEE_ID  FIRST_NAME  SALARY      PHONE_NUMBER  EMAIL       JOB_ID
-----------  ----------  ----------  ------------  ----------  ----------
100          Steven      27600       515.123.4567  SKING       AD_PRES
101          Neena       19550       515.123.4568  NKOCHHAR    AD_VP
102          Lex         19550       515.123.4569  LDEHAAN     AD_VP
103          Alexander   9000        590.423.4567  AHUNOLD     IT_PROG
104          Bruce       6000        590.423.4568  BERNST      IT_PROG
105          David       4800        590.423.4569  DAUSTIN     IT_PROG
106          Valli       4800        590.423.4560  VPATABAL    IT_PROG
107          Diana       4200        590.423.5567  DLORENTZ    IT_PROG
108          Nancy       12000       515.124.4569  NGREENBE    FI_MGR
109          Daniel      9000        515.124.4169  DFAVIET     FI_ACCOUNT

**Got**
EMPLOYEE_ID  FIRST_NAME  SALARY      PHONE_NUMBER  EMAIL       JOB_ID
-----------  ----------  ----------  ------------  ----------  ----------
100          Steven      27600       515.123.4567  SKING       AD_PRES
101          Neena       19550       515.123.4568  NKOCHHAR    AD_VP
102          Lex         19550       515.123.4569  LDEHAAN     AD_VP
103          Alexander   9000        590.423.4567  AHUNOLD     IT_PROG
104          Bruce       6000        590.423.4568  BERNST      IT_PROG
105          David       4800        590.423.4569  DAUSTIN     IT_PROG
106          Valli       4800        590.423.4560  VPATABAL    IT_PROG
107          Diana       4200        590.423.5567  DLORENTZ    IT_PROG
108          Nancy       12000       515.124.4569  NGREENBE    FI_MGR
109          Daniel      9000        515.124.4169  DFAVIET     FI_ACCOUNT
```
*Question 5*
---
--Increase the reorder level by 30% for products from 'Food' category having quantity in stock less than 50% of existing reorder level in the products table
name               type
--------------  ----------
product_id         INT
product_name       VARCHAR(10)
category           VARCHAR(50)
cost_price         DECIMAL(10)
sell_price         DECIMAL(10)
reorder_lvl        INT
quantity              INT
supplier_id           INT

sql
``` 
UPDATE products
SET reorder_lvl = reorder_lvl * 1.30
WHERE category = 'Food' AND quantity < reorder_lvl * 0.90;
```

*Output:*
```
Test
select changes();
changes()
----------
4
changes()
----------
4
SELECT*FROM Products WHERE supplier_id = 10;

***Expexted**
product_id  product_name  category    cost_price  sell_price  reorder_lvl  quantity    supplier_id
----------  ------------  ----------  ----------  ----------  -----------  ----------  -----------
6           Sandwich      Food        60          80          26           5           10
7           Chat Items    Food        85          100         13           2           10
8           Chapathi      Food        85          100         13           0           10
9           Idly          Food        85          100         13           3           10

**Got**
product_id  product_name  category    cost_price  sell_price  reorder_lvl  quantity    supplier_id
----------  ------------  ----------  ----------  ----------  -----------  ----------  -----------
6           Sandwich      Food        60          80          26           5           10
7           Chat Items    Food        85          100         13           2           10
8           Chapathi      Food        85          100         13           0           10
9           Idly          Food        85          100         13           3           10
```
*Question 6*
---
-- Write a SQL query to remove rows from the table 'customer' with the following condition -

1. 'cust_country' must be 'India',

2. 'cus_city' must not be 'Chennai',

Sample table: Customer

+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+  
|CUST_CODE  | CUST_NAME   | CUST_CITY   | WORKING_AREA | CUST_COUNTRY | GRADE | OPENING_AMT | RECEIVE_AMT | PAYMENT_AMT |OUTSTANDING_AMT| PHONE_NO     | AGENT_CODE |
+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+
| C00013    | Holmes      | London      | London       | UK           |     2 |     6000.00 |     5000.00 |     7000.00 |       4000.00 | BBBBBBB      | A003       |
| C00001    | Micheal     | New York    | New York     | USA          |     2 |     3000.00 |     5000.00 |     2000.00 |       6000.00 | CCCCCCC      | A008       |
| C00020    | Albert      | New York    | New York     | USA          |     3 |     5000.00 |     7000.00 |     6000.00 |       6000.0

sql
```
DELETE FROM customer
WHERE cust_country = 'India' AND cust_city <> 'Chennai';
```

*Output:*
```
***TEST***
SELECT * FROM customer WHERE cust_country='India';

***Expected***
CUST_CODE   CUST_NAME   CUST_CITY   WORKING_AREA  CUST_COUNTRY  GRADE       OPENING_AMT  RECEIVE_AMT  PAYMENT_AMT  OUTSTANDING_AMT  PHONE_NO    AGENT_CODE
----------  ----------  ----------  ------------  ------------  ----------  -----------  -----------  -----------  ---------------  ----------  ----------
C00025      Ravindran   Bangalore   Bangalore     India         2           5000         7000         4000         8000             AVAVAVA     A011
C00019      Yearannaid  Chennai     Chennai       India         1           8000         7000         7000         8000             ZZZZBFV     A010
C00005      Sasikant    Mumbai      Mumbai        India         1           7000         11000        7000         11000            147-258963  A002
C00007      Ramanathan  Chennai     Chennai       India         1           7000         11000        9000         9000             GHRDWSD     A010
C00022      Avinash     Mumbai      Mumbai        India         2           7000         11000        9000         9000             113-123456  A002
C00017      Srinivas    Bangalore   Bangalore     India         2           8000         4000         3000         9000             AAAAAAB     A007
C00009      Ramesh      Mumbai      Mumbai        India         3           8000         7000         3000         12000            Phone No    A002
C00014      Rangarappa  Bangalore   Bangalore     India         2           8000         11000        7000         12000            AAAATGF     A001
C00016      Venkatpati  Bangalore   Bangalore     India         2           8000         11000        7000         12000            JRTVFDD     A007
C00011      Sundariya   Chennai     Chennai       India         3           7000         11000        7000         11000            PPHGRTS     A010
CUST_CODE   CUST_NAME    CUST_CITY   WORKING_AREA  CUST_COUNTRY  GRADE       OPENING_AMT  RECEIVE_AMT  PAYMENT_AMT  OUTSTANDING_AMT  PHONE_NO    AGENT_CODE
----------  -----------  ----------  ------------  ------------  ----------  -----------  -----------  -----------  ---------------  ----------  ----------
C00019      Yearannaidu  Chennai     Chennai       India         1           8000         7000         7000         8000             ZZZZBFV     A010
C00007      Ramanathan   Chennai     Chennai       India         1           7000         11000        9000         9000             GHRDWSD     A010
C00011      Sundariya    Chennai     Chennai       India         3           7000         11000        7000         11000            PPHGRTS     A010

***Got***
CUST_CODE   CUST_NAME   CUST_CITY   WORKING_AREA  CUST_COUNTRY  GRADE       OPENING_AMT  RECEIVE_AMT  PAYMENT_AMT  OUTSTANDING_AMT  PHONE_NO    AGENT_CODE
----------  ----------  ----------  ------------  ------------  ----------  -----------  -----------  -----------  ---------------  ----------  ----------
C00025      Ravindran   Bangalore   Bangalore     India         2           5000         7000         4000         8000             AVAVAVA     A011
C00019      Yearannaid  Chennai     Chennai       India         1           8000         7000         7000         8000             ZZZZBFV     A010
C00005      Sasikant    Mumbai      Mumbai        India         1           7000         11000        7000         11000            147-258963  A002
C00007      Ramanathan  Chennai     Chennai       India         1           7000         11000        9000         9000             GHRDWSD     A010
C00022      Avinash     Mumbai      Mumbai        India         2           7000         11000        9000         9000             113-123456  A002
C00017      Srinivas    Bangalore   Bangalore     India         2           8000         4000         3000         9000             AAAAAAB     A007
C00009      Ramesh      Mumbai      Mumbai        India         3           8000         7000         3000         12000            Phone No    A002
C00014      Rangarappa  Bangalore   Bangalore     India         2           8000         11000        7000         12000            AAAATGF     A001
C00016      Venkatpati  Bangalore   Bangalore     India         2           8000         11000        7000         12000            JRTVFDD     A007
C00011      Sundariya   Chennai     Chennai       India         3           7000         11000        7000         11000            PPHGRTS     A010
CUST_CODE   CUST_NAME    CUST_CITY   WORKING_AREA  CUST_COUNTRY  GRADE       OPENING_AMT  RECEIVE_AMT  PAYMENT_AMT  OUTSTANDING_AMT  PHONE_NO    AGENT_CODE
----------  -----------  ----------  ------------  ------------  ----------  -----------  -----------  -----------  ---------------  ----------  ----------
C00019      Yearannaidu  Chennai     Chennai       India         1           8000         7000         7000         8000             ZZZZBFV     A010
C00007      Ramanathan   Chennai     Chennai       India         1           7000         11000        9000         9000             GHRDWSD     A010
C00011      Sundariya    Chennai     Chennai       India         3           7000         11000        7000         11000            PPHGRTS     A010
```
*Question 7*
---
-- Write a SQL query to Delete All Doctors whose ID ranges from 2 to 4.

Sample table: Doctors

attributes : doctor_id, first_name, last_name, specialization
For example:

Test	Result
SELECT * FROM doctors;
doctor_id   first_name  last_name   specialization
----------  ----------  ----------  --------------
1           John        Smith       Cardiology
2           Emily       Johnson     Orthopedics
3           Michael     Brown       Pediatrics
doctor_id   first_name  last_name   specialization
----------  ----------  ----------  --------------
1           John        Smith       Cardiology


sql
```
DELETE FROM Doctors
WHERE doctor_id BETWEEN 2 AND 4;
```

*Output:*
```
***TEST**
SELECT * FROM doctors;

***Expected**
doctor_id   first_name  last_name   specialization
----------  ----------  ----------  --------------
1           John        Smith       Cardiology
2           Emily       Johnson     Orthopedics
3           Michael     Brown       Pediatrics
doctor_id   first_name  last_name   specialization
----------  ----------  ----------  --------------
1           John        Smith       Cardiology

*Got**
doctor_id   first_name  last_name   specialization
----------  ----------  ----------  --------------
1           John        Smith       Cardiology
2           Emily       Johnson     Orthopedics
3           Michael     Brown       Pediatrics
doctor_id   first_name  last_name   specialization
----------  ----------  ----------  --------------
1           John        Smith       Cardiology

```
*Question 8*
---
-- Write a SQL query to Delete customers from 'customer' table where 'CUST_NAME' contains the substring 'Holmes'.

Sample table: Customer

+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+  
|CUST_CODE  | CUST_NAME   | CUST_CITY   | WORKING_AREA | CUST_COUNTRY | GRADE | OPENING_AMT | RECEIVE_AMT | PAYMENT_AMT |OUTSTANDING_AMT| PHONE_NO     | AGENT_CODE |
+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+
| C00013    | Holmes      | London      | London       | UK           |     2 |     6000.00 |     5000.00 |     7000.00 |       4000.00 | BBBBBBB      | A003       |
| C00001    | Micheal     | New York    | New York     | USA          |     2 |     3000.00 |     5000.00 |     2000.00 |       6000.00 | CCCCCCC      | A008       |
| C00020    | Albert      | New York    | New York     | USA          |     3 |     5000.00 |     7000.00 |     6000.00 |       6000.00 | BBBB

sql
``` 
DELETE FROM customer
WHERE CUST_NAME LIKE '%Holmes%';
```

*Output:*
```
***Test**
select changes();

***Expected**
CUST_CODE   CUST_NAME   CUST_CITY   WORKING_AREA  CUST_COUNTRY  GRADE       OPENING_AMT  RECEIVE_AMT  PAYMENT_AMT  OUTSTANDING_AMT  PHONE_NO    AGENT_CODE
----------  ----------  ----------  ------------  ------------  ----------  -----------  -----------  -----------  ---------------  ----------  ----------
C00013      Holmes      London      London        UK            2           6000         5000         7000         4000             BBBBBBB     A003
changes()
----------
1

***Got***
CUST_CODE   CUST_NAME   CUST_CITY   WORKING_AREA  CUST_COUNTRY  GRADE       OPENING_AMT  RECEIVE_AMT  PAYMENT_AMT  OUTSTANDING_AMT  PHONE_NO    AGENT_CODE
----------  ----------  ----------  ------------  ------------  ----------  -----------  -----------  -----------  ---------------  ----------  ----------
C00013      Holmes      London      London        UK            2           6000         5000         7000         4000             BBBBBBB     A003
```
*Question 9*
---
-- Write a SQL query to remove rows from the table 'customer' with the following condition -

1. 'cust_city' should begin with the letter 'L',

Sample table: Customer

+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+  
|CUST_CODE  | CUST_NAME   | CUST_CITY   | WORKING_AREA | CUST_COUNTRY | GRADE | OPENING_AMT | RECEIVE_AMT | PAYMENT_AMT |OUTSTANDING_AMT| PHONE_NO     | AGENT_CODE |
+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+
| C00013    | Holmes      | London      | London       | UK           |     2 |     6000.00 |     5000.00 |     7000.00 |       4000.00 | BBBBBBB      | A003       |
| C00001    | Micheal     | New York    | New York     | USA          |     2 |     3000.00 |     5000.00 |     2000.00 |       6000.00 | CCCCCCC      | A008       |
| C00020    | Albert      | New York    | New York     | USA          |     3 |     5000.00 |     7000.00 |     6000.00 |       6000.00

sql
```
DELETE FROM customer
WHERE SUBSTR(cust_city, 1, 1) = 'L';
```

*Output:*
```
***test***
SELECT * FROM customer WHERE cust_country='UK';

***Expected***
CUST_CODE   CUST_NAME   CUST_CITY   WORKING_AREA  CUST_COUNTRY  GRADE       OPENING_AMT  RECEIVE_AMT  PAYMENT_AMT  OUTSTANDING_AMT  PHONE_NO    AGENT_CODE
----------  ----------  ----------  ------------  ------------  ----------  -----------  -----------  -----------  ---------------  ----------  ----------
C00013      Holmes      London      London        UK            2           6000         5000         7000         4000             BBBBBBB     A003
C00024      Cook        London      London        UK            2           4000         9000         7000         6000             FSDDSDF     A006
C00015      Stuart      London      London        UK            1           6000         8000         3000         11000            GFSGERS     A003
C00023      Karl        London      London        UK            0           4000         6000         7000         3000             AAAABAA     A006
C00010      Charles     Hampshair   Hampshair     UK            3           6000         4000         5000         5000             MMMMMMM     A009
CUST_CODE   CUST_NAME   CUST_CITY   WORKING_AREA  CUST_COUNTRY  GRADE       OPENING_AMT  RECEIVE_AMT  PAYMENT_AMT  OUTSTANDING_AMT  PHONE_NO    AGENT_CODE
----------  ----------  ----------  ------------  ------------  ----------  -----------  -----------  -----------  ---------------  ----------  ----------
C00010      Charles     Hampshair   Hampshair     UK            3           6000         4000         5000         5000             MMMMMMM     A009

***Got***
CUST_CODE   CUST_NAME   CUST_CITY   WORKING_AREA  CUST_COUNTRY  GRADE       OPENING_AMT  RECEIVE_AMT  PAYMENT_AMT  OUTSTANDING_AMT  PHONE_NO    AGENT_CODE
----------  ----------  ----------  ------------  ------------  ----------  -----------  -----------  -----------  ---------------  ----------  ----------
C00013      Holmes      London      London        UK            2           6000         5000         7000         4000             BBBBBBB     A003
C00024      Cook        London      London        UK            2           4000         9000         7000         6000             FSDDSDF     A006
C00015      Stuart      London      London        UK            1           6000         8000         3000         11000            GFSGERS     A003
C00023      Karl        London      London        UK            0           4000         6000         7000         3000             AAAABAA     A006
C00010      Charles     Hampshair   Hampshair     UK            3           6000         4000         5000         5000             MMMMMMM     A009
CUST_CODE   CUST_NAME   CUST_CITY   WORKING_AREA  CUST_COUNTRY  GRADE       OPENING_AMT  RECEIVE_AMT  PAYMENT_AMT  OUTSTANDING_AMT  PHONE_NO    AGENT_CODE
----------  ----------  ----------  ------------  ------------  ----------  -----------  -----------  -----------  ---------------  ----------  ----------
C00010      Charles     Hampshair   Hampshair     UK            3           6000         4000         5000         5000             MMMMMMM     A009
```
**Question 10**
---
-- Write a SQL query to Delete All Doctors with a NULL Last Name

Sample table: Doctors

attributes : doctor_id, first_name, last_name, specialization
For example:

Test	Result
SELECT * FROM doctors;
doctor_id   first_name  last_name   specialization
----------  ----------  ----------  --------------
1           John        Smith       Cardiology
2           Emily       Johnson     Orthopedics
3           Michael     Brown       Pediatrics
4           Febin                   Cardiology
doctor_id   first_name  last_name   specialization
----------  ----------  ----------  --------------
1           John        Smith       Cardiology
2           Emily       Johnson     Orthopedics
3           Michael     Brown       Pediatrics

sql
```
DELETE FROM Doctors
WHERE last_name IS NULL;
```

**Output:**
```
**Test**
SELECT * FROM doctors;

**Expected**
doctor_id   first_name  last_name   specialization
----------  ----------  ----------  --------------
1           John        Smith       Cardiology
2           Emily       Johnson     Orthopedics
3           Michael     Brown       Pediatrics
4           Febin                   Cardiology
doctor_id   first_name  last_name   specialization
----------  ----------  ----------  --------------
1           John        Smith       Cardiology
2           Emily       Johnson     Orthopedics
3           Michael     Brown       Pediatrics

**Got**
doctor_id   first_name  last_name   specialization
----------  ----------  ----------  --------------
1           John        Smith       Cardiology
2           Emily       Johnson     Orthopedics
3           Michael     Brown       Pediatrics
4           Febin                   Cardiology
doctor_id   first_name  last_name   specialization
----------  ----------  ----------  --------------
1           John        Smith       Cardiology
2           Emily       Johnson     Orthopedics
3           Michael     Brown       Pediatrics
```
## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully. 
