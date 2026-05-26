# ER Diagram Workshop – Submission Template

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
*Paste or attach your diagram here*  

<img width="761" height="571" alt="er_1" src="https://github.com/user-attachments/assets/ec4ea132-3406-425e-96ce-7b23d9e044fc" />


### Entities and Attributes

| Entity     | Attributes (PK, FK)                                                              | Notes                         |
| ---------- | -------------------------------------------------------------------------------- | ----------------------------- |
| Member     | **Member_ID (PK)**, Name, Membership_Type, Start_Date                            | Gym member details            |
| Program    | **Program_ID (PK)**, Program_Name                                                | Yoga, Zumba, Weight Training  |
| Trainer    | **Trainer_ID (PK)**, Name, Specialization                                        | Trainers working in gym       |
| Session    | **Session_ID (PK)**, Session_Date, Session_Time, Trainer_ID (FK), Member_ID (FK) | Personal training session     |
| Attendance | **Attendance_ID (PK)**, Member_ID (FK), Session_ID (FK), Status                  | Records attendance            |
| Payment    | **Payment_ID (PK)**, Member_ID (FK), Amount, Payment_Date, Payment_Type          | Membership or session payment |


### Relationships and Constraints

| Relationship                    | Cardinality | Participation | Notes                               |
| ------------------------------- | ----------- | ------------- | ----------------------------------- |
| Member — joins — Program        | M:N         | Partial       | Members can join multiple programs  |
| Trainer — assigned_to — Program | M:N         | Partial       | Programs may have multiple trainers |
| Member — books — Session        | 1:M         | Partial       | Member can book many sessions       |
| Trainer — conducts — Session    | 1:M         | Total         | Trainer conducts sessions           |
| Session — records — Attendance  | 1:M         | Total         | Attendance for each session         |
| Member — makes — Payment        | 1:M         | Total         | Payments for membership or session  |


### Assumptions

- Each member has a unique Member_ID used to identify them in the system.

- A member can join multiple fitness programs, and each program can have multiple members.

- A trainer may handle multiple programs, and a program may have more than one trainer.

- Personal training sessions are booked by one member with one trainer at a specific time.

- Payments can be made for both membership registration and personal training sessions.

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

<img width="766" height="572" alt="er_2" src="https://github.com/user-attachments/assets/09fa2330-0542-485e-b522-875aec84b87a" />


### Entities and Attributes

| Entity  | Attributes (PK, FK)                                                    | Notes                  |
| ------- | ---------------------------------------------------------------------- | ---------------------- |
| Member  | **Member_ID (PK)**, Name, Address, Phone                               | Library member         |
| Book    | **Book_ID (PK)**, Title, Author, Category                              | Book details           |
| Loan    | **Loan_ID (PK)**, Member_ID (FK), Book_ID (FK), Loan_Date, Return_Date | Borrowing records      |
| Event   | **Event_ID (PK)**, Event_Name, Event_Date                              | Cultural events        |
| Speaker | **Speaker_ID (PK)**, Name, Expertise                                   | Event speakers/authors |
| Room    | **Room_ID (PK)**, Room_Name, Capacity                                  | Rooms for events/study |
| Fine    | **Fine_ID (PK)**, Loan_ID (FK), Amount                                 | Late return fine       |


### Relationships and Constraints

| Relationship               | Cardinality | Participation | Notes                             |
| -------------------------- | ----------- | ------------- | --------------------------------- |
| Member — borrows — Book    | M:N         | Partial       | Members can borrow multiple books |
| Member — registers — Event | M:N         | Partial       | Members attend events             |
| Event — has — Speaker      | 1:M         | Total         | Event may have many speakers      |
| Event — booked_in — Room   | M:1         | Total         | Event held in one room            |
| Loan — generates — Fine    | 1:1         | Partial       | Fine for overdue books            |


### Assumptions

- Each member and book is identified by a unique Member_ID and Book_ID.

- A member can borrow multiple books, but each book loan record corresponds to one member at a time.

- A book can be borrowed multiple times over time but only by one member during a loan period.

- Events organized by the library may have multiple speakers/authors.

- A fine is generated only when a book is returned after the due date.

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

<img width="760" height="567" alt="er_3" src="https://github.com/user-attachments/assets/3e7c81f2-745e-45f3-a222-c5c24c7e31a0" />


### Entities and Attributes

| Entity      | Attributes (PK, FK)                                                 | Notes               |
| ----------- | ------------------------------------------------------------------- | ------------------- |
| Customer    | **Customer_ID (PK)**, Name, Phone                                   | Restaurant customer |
| Reservation | **Reservation_ID (PK)**, Date, Time, Guests, Customer_ID (FK)       | Table reservation   |
| Table       | **Table_ID (PK)**, Capacity                                         | Restaurant tables   |
| Order       | **Order_ID (PK)**, Reservation_ID (FK), Order_Time                  | Food order          |
| Dish        | **Dish_ID (PK)**, Dish_Name, Price, Category                        | Food items          |
| Bill        | **Bill_ID (PK)**, Reservation_ID (FK), Total_Amount, Service_Charge | Final bill          |
| Waiter      | **Waiter_ID (PK)**, Name                                            | Restaurant staff    |


### Relationships and Constraints

| Relationship                      | Cardinality | Participation | Notes                            |
| --------------------------------- | ----------- | ------------- | -------------------------------- |
| Customer — makes — Reservation    | 1:M         | Partial       | Customer can reserve many tables |
| Reservation — assigned_to — Table | M:1         | Total         | Reservation for a table          |
| Reservation — places — Order      | 1:M         | Total         | Multiple orders                  |
| Order — contains — Dish           | M:N         | Total         | Many dishes per order            |
| Reservation — generates — Bill    | 1:1         | Total         | One bill per reservation         |
| Waiter — serves — Reservation     | 1:M         | Partial       | Waiter serves many tables        |


### Assumptions

- Each customer, reservation, and order has a unique identifier in the system.

- A customer can make multiple reservations, but each reservation belongs to only one customer.

- Each reservation is assigned to one table, while a table can serve multiple reservations at different times.

- An order may contain multiple dishes, and the same dish can appear in multiple orders.

- A single bill is generated per reservation, including food items and service charges.

---

## Instructions for Students

1. Complete **all three scenarios** (A, B, C).  
2. Identify entities, relationships, and attributes for each.  
3. Draw ER diagrams using **draw.io / diagrams.net** or hand-drawn & scanned.  
4. Fill in all tables and assumptions for each scenario.  
5. Export the completed Markdown (with diagrams) as **a single PDF**
