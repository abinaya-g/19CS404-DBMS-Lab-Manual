# ER DIAGRAM WORKSHOP(EXPERIMENT)
## NAME : VISHWA V
## REG NO : 212224110062

## Objective
To understand and apply ER modeling concepts by creating ER diagrams for real-world applications.

## Purpose
Gain hands-on experience in designing ER diagrams that represent database structure including entities, relationships, attributes, and constraints.

---

# Scenario A: City Fitness Club Management

**Business Context:**  
FlexiFit Gym wants a database to manage its members, trainers, and fitness programs.

**Requirements:**  
- Members register with name, membership type, and start date.  
- Each member can join multiple programs (Yoga, Zumba, Weight Training).  
- Trainers assigned to programs; a program may have multiple trainers.  
- Members may book personal training sessions with trainers.  
- Attendance recorded for each session.  
- Payments tracked for memberships and sessions.

### ER Diagram:
![Workshop - ER Diagram1 jpg (1)](https://github.com/user-attachments/assets/1d1fc4df-bea6-480d-b373-0bd69951edee)


### Entities and Attributes
```

Entity        | Attributes                                               | Primary Key   | Foreign Key
-----------------------------------------------------------------------------------------
MEMBER        | member_id, name, membership_type, start_date             | member_id     | -
TRAINER       | trainer_id, trainer_name, specialization, phone_number   | trainer_id | -
PROGRAM       | program_id, program_name, duration, schedule             | program_id    | -
SESSION       | session_id, session_date, session_time                   | session_id    | member_id
PAYMENT       | payment_id, payment_type, amount, payment_date           | payment_id | member_id
ATTENDANCE    | attendance_id, status                                    | attendance_id | session_id
```

### Relationships and Constraints
```

Relationship | Entities Involved        | Cardinality | Participation | Notes
-----------------------------------------------------------------------------------------
ASSIGNED_TO  | TRAINER – PROGRAM       | M : N       | Partial       | A trainer can teach many programs and a program can have many trainers
JOINS        | MEMBER – PROGRAM        | M : N       | Partial       | Members can join multiple fitness programs
BOOKS        | MEMBER – SESSION        | 1 : M       | Partial       | A member can book many personal training sessions
ATTENDS      | SESSION – ATTENDANCE    | 1 : N       | Total         | Each session has multiple attendance records
MAKES        | MEMBER – PAYMENT        | 1 : N       | Partial       | Members can make multiple payments
```

### Assumptions
- Each member has a unique Member_ID.
- Trainers can teach multiple programs.
- Programs can have multiple trainers.
- Members may book multiple personal training sessions.
- Payments may include membership fees or session fees.
- Attendance status can be Present or Absent.
---

# Scenario B: City Library Event & Book Lending System

**Business Context:**  
The Central Library wants to manage book lending and cultural events.

**Requirements:**  
- Members borrow books, with loan and return dates tracked.  
- Each book has title, author, and category.  
- Library organizes events; members can register.  
- Each event has one or more speakers/authors.  
- Rooms are booked for events and study.  
- Overdue fines apply for late returns.

### ER Diagram:
![Workshop - ER Diagram_page-0002 jpg (1)](https://github.com/user-attachments/assets/6a59978b-8679-446e-af9b-febca67138a9)


### Entities and Attributes
```

Entity     | Attributes                                   | Primary Key | Foreign Key
--------------------------------------------------------------------------------------
MEMBER     | M_ID, Name, Email, Phno, Addr                | M_ID        | -
BOOK       | Book_ID, Title, Author, Category             | Book_ID     | -
LOAN       | Loan_ID, Loan_Date, Return_Date, F_Amt       | Loan_ID     | M_ID, Book_ID
EVENT      | Event_ID, Event_Name, Date, Time             | Event_ID    | -
SPEAKER    | Speaker_ID, Name, Expertise                  | Speaker_ID  | Event_ID
ROOM       | Room_ID, Room_Name, Capacity                 | Room_ID     | Event_ID
```

### Relationships and Constraints
```

Relationship | Entities Involved      | Cardinality | Participation | Notes
---------------------------------------------------------------------------------------
BORROWS      | MEMBER – LOAN         | 1 : M       | Partial       | A member can borrow many books
LOAN_BOOK    | LOAN – BOOK           | M : 1       | Total         | Each loan refers to one specific book
REGISTERS    | MEMBER – EVENT        | M : N       | Partial       | Members can register for multiple events
HAS          | EVENT – SPEAKER       | 1 : M       | Total         | Each event may have one or more speakers
CONDUCTED    | EVENT – ROOM          | M : 1       | Total         | Each event is conducted in one room
```

### Assumptions
- Each book has a unique Book_ID.
- Members can borrow multiple books.
- Overdue books generate fine amount (F_Amt).
- Events may have multiple speakers
- Each event is conducted in one room only.
- Members can register for multiple events.
---

# Scenario C: Restaurant Table Reservation & Ordering

**Business Context:**  
A popular restaurant wants to manage reservations, orders, and billing.

**Requirements:**  
- Customers can reserve tables or walk in.  
- Each reservation includes date, time, and number of guests.  
- Customers place food orders linked to reservations.  
- Each order contains multiple dishes; dishes belong to categories (starter, main, dessert).  
- Bills generated per reservation, including food and service charges.  
- Waiters assigned to serve reservations.

### ER Diagram:
*Paste or attach your diagram here*  
![ER Diagram](er_diagram_restaurant.png)

### Entities and Attributes

| Entity | Attributes (PK, FK) | Notes |
|--------|--------------------|-------|
|        |                    |       |
|        |                    |       |
|        |                    |       |
|        |                    |       |
|        |                    |       |

### Relationships and Constraints

| Relationship | Cardinality | Participation | Notes |
|--------------|------------|---------------|-------|
|              |            |               |       |
|              |            |               |       |
|              |            |               |       |

### Assumptions
- 
- 
- 

---

## Instructions for Students

1. Complete **all three scenarios** (A, B, C).  
2. Identify entities, relationships, and attributes for each.  
3. Draw ER diagrams using **draw.io / diagrams.net** or hand-drawn & scanned.  
4. Fill in all tables and assumptions for each scenario.  
5. Export the completed Markdown (with diagrams) as **a single PDF**
