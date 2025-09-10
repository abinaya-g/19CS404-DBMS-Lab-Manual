# Experiment 6: Joins

## AIM
To study and implement different types of joins.

## THEORY

SQL Joins are used to combine records from two or more tables based on a related column.

### 1. INNER JOIN
Returns records with matching values in both tables.

**Syntax:**
```sql
SELECT columns
FROM table1
INNER JOIN table2
ON table1.column = table2.column;
```

### 2. LEFT JOIN
Returns all records from the left table, and matched records from the right.

**Syntax:**

```sql
SELECT columns
FROM table1
LEFT JOIN table2
ON table1.column = table2.column;
```
### 3. RIGHT JOIN
Returns all records from the right table, and matched records from the left.

**Syntax:**

```sql
SELECT columns
FROM table1
RIGHT JOIN table2
ON table1.column = table2.column;
```
### 4. FULL OUTER JOIN
Returns all records when there is a match in either left or right table.

**Syntax:**

```sql
SELECT columns
FROM table1
FULL OUTER JOIN table2
ON table1.column = table2.column;
```

**Question 1**
--
--![Screenshot 2025-04-29 174738](https://github.com/user-attachments/assets/34425bc2-e262-447b-a9d0-06b0527dac41)


```sql
-- ![Screenshot 2025-04-29 174858](https://github.com/user-attachments/assets/77abfac4-2344-481a-ba97-a22894c86b0c)

```

**Output:**

![Screenshot 2025-04-29 174918](https://github.com/user-attachments/assets/15a87e6d-fa2a-48de-9e1f-72b98a4bb724)


**Question 2**
---
-- ![Screenshot 2025-04-29 174935](https://github.com/user-attachments/assets/a6e4ab6f-eade-47ec-a111-fc35fd76ec94)


```sql
-- ![Screenshot 2025-04-29 174949](https://github.com/user-attachments/assets/bf59bca5-026b-4e50-8aa5-e3a36dbe8eb2)

```

**Output:**
![Screenshot 2025-04-29 175002](https://github.com/user-attachments/assets/58282248-ffc9-48fb-9206-062a2e97408c)

**Question 3**
---
-- ![Screenshot 2025-04-29 175112](https://github.com/user-attachments/assets/90fdc22b-d379-4b00-8f8f-68cf78a265eb)


```sql
-- ![Screenshot 2025-04-29 175120](https://github.com/user-attachments/assets/fb1c85ba-104f-4b23-9e7e-76e02146859a)

```

**Output:**

![Screenshot 2025-04-29 175130](https://github.com/user-attachments/assets/d64a7f56-f1a5-4309-a7dc-2959bfea9e56)


**Question 4**
---
-- ![Screenshot 2025-04-29 175137](https://github.com/user-attachments/assets/dccaa43b-a421-427a-b555-7db8978a35fa)


```sql
-- ![Screenshot 2025-04-29 175145](https://github.com/user-attachments/assets/266eafc1-083b-4031-9c30-434bfa01c7ec)

```

**Output:**

![Screenshot 2025-04-29 175158](https://github.com/user-attachments/assets/219a8a72-7b00-451c-97df-c830e207fb4c)


**Question 5**
---
-- ![Screenshot 2025-04-29 175209](https://github.com/user-attachments/assets/2397b313-813b-4907-8d18-ccfe8d2cd55a)


```sql
--![Screenshot 2025-04-29 175218](https://github.com/user-attachments/assets/8aee1932-a25a-4358-ad8f-299172ec7844)

```

**Output:**

![Screenshot 2025-04-29 175224](https://github.com/user-attachments/assets/bfff1091-c895-4cc7-a3e1-a2fe09be29c3)


**Question 6**
---![Screenshot 2025-04-29 175237](https://github.com/user-attachments/assets/0ff49c31-0dc1-40f2-be50-6793f9520755)

```sql
-- ![Screenshot 2025-04-29 175244](https://github.com/user-attachments/assets/2795665e-b921-44a2-a86f-dae9aaaceee9)

```

**Output:**

![Screenshot 2025-04-29 175258](https://github.com/user-attachments/assets/4e09a5da-f38c-43ef-b0cb-4645aebbb64b)


**Question 7**
---
-- ![Screenshot 2025-04-29 175310](https://github.com/user-attachments/assets/4f50677a-9d6f-458b-bfee-b94e89556b0a)


```sql
--
```![Screenshot 2025-04-29 175319](https://github.com/user-attachments/assets/7f3756a1-61f4-4848-9b54-df600d196ae6)


**Output:**
![Screenshot 2025-04-29 175327](https://github.com/user-attachments/assets/05f7aa3b-4fe4-42cd-8b45-d8a69194c874)

**Question 8**
---
-- ![Screenshot 2025-04-29 175339](https://github.com/user-attachments/assets/3b873243-9230-47b3-bbd1-9f1bd2a3d035)


```sql
-- ![Screenshot 2025-04-29 175346](https://github.com/user-attachments/assets/76c39906-ba15-4a87-80c0-58eb2bce68af)

```

**Output:**

![Screenshot 2025-04-29 175357](https://github.com/user-attachments/assets/143d1372-29f1-4366-ac02-b05667d1b37e)


**Question 9**
---![Screenshot 2025-04-29 175406](https://github.com/user-attachments/assets/b8101646-6957-4108-87a9-21604358efbd)


```sql
```![Screenshot 2025-04-29 175412](https://github.com/user-attachments/assets/af16bfd7-54bd-4fcd-914e-fbe14d6985ca)


**Output:**

![Screenshot 2025-04-29 175420](https://github.com/user-attachments/assets/1e5cc84a-098b-4649-bf24-1c1b55320772)


**Question 10**
---
-- ![Screenshot 2025-04-29 175428](https://github.com/user-attachments/assets/8572a81c-8f36-4528-954c-1c568b7896cf)


```sql
```![Screenshot 2025-04-29 175436](https://github.com/user-attachments/assets/32af4738-d8e5-4e15-bf12-7f4c96e6c779)


**Output:**

![Screenshot 2025-04-29 175443](https://github.com/user-attachments/assets/fe2c59be-9051-4063-8487-7050bd0d528c)



## RESULT
Thus, the SQL queries to implement different types of joins have been executed successfully.
