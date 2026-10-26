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
[Sashtitha_Er1.pdf](https://github.com/user-attachments/files/33960612/Sashtitha_Er1.pdf)

![ER Diagram](er_diagram_fitness.png)


### Entities and Attributes

| Entity | Attributes |
|---|---|
| MEMBER | Member_ID (PK), Name, Membership_Type, Start_Date, Phone |
| PROGRAM | Program_ID (PK), Program_Name, Description |
| TRAINER | Trainer_ID (PK), Trainer_Name, Phone, Specialization |
| PERSONAL TRAINING SESSION | Session_ID (PK), Date, Time, Duration |
| ATTENDANCE | Attendance_ID (PK), Date, Status |
| PAYMENT | Payment_ID (PK), Amount, Date, Mode, Payment_Type |

### Relationships and Constraints

| Relationship | Entities | Cardinality |
|---|---|---|
| Enrolls | MEMBER – PROGRAM | M:N |
| Handled By | PROGRAM – TRAINER | M:N |
| Books | MEMBER – PERSONAL_TRAINING_SESSION | 1:N |
| Conducts | TRAINER – PERSONAL_TRAINING_SESSION | 1:N |
| Marks | MEMBER – ATTENDANCE | 1:N |
| Recorded For | ATTENDANCE – PERSONAL_TRAINING_SESSION | N:1 |
| Pays | MEMBER – PAYMENT | 1:N |

### Assumptions
- Each member is assigned a unique Member_ID and can enroll in multiple fitness programs.
- A program can be handled by multiple trainers, and a trainer can handle multiple programs
- Each personal training session is booked by one member and conducted by one trainer. A member can book multiple sessions.

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
*Paste or attach your diagram here* 
[Sashtitha_ER2.pdf](https://github.com/user-attachments/files/33960618/Sashtitha_ER2.pdf)

![ER Diagram](er_diagram_library.png)

### Entities and Attributes

| Entity | Attributes |
|---|---|
| MEMBER | Member_ID (PK), Name, Phone, Email, Address |
| BOOK | Book_ID (PK), Title, Author, Category |
| LOAN | Loan_ID (PK), Loan_Date, Due_Date, Return_Date |
| FINE | Fine_ID (PK), Amount, Fine_Date, Payment_Status |
| EVENT | Event_ID (PK), Event_Name, Event_Date, Description |
| SPEAKER | Speaker_ID (PK), Speaker_Name, Specialization |
| ROOM | Room_ID (PK), Room_Name, Capacity, Room_Type |
### Relationships and Constraints

| Relationship | Entities | Cardinality | Explanation |
|---|---|---|---|
| Borrows | MEMBER – LOAN | 1:N | A member can borrow many books over time |
| For | LOAN – BOOK | N:1 | Each loan refers to one book |
| Has Fine | LOAN – FINE | 1:0..1 | A loan may have an overdue fine |
| Registers | MEMBER – EVENT | M:N | Members can register for multiple events |
| Features | EVENT – SPEAKER | M:N | An event may have multiple speakers |
| Booked In | EVENT – ROOM | N:1 | Each event is assigned to one room |
| Reserves | MEMBER – ROOM | M:N | Members can reserve rooms for study |

### Assumptions
- Each member and each book has a unique ID, and a member can borrow multiple books over time.
- Each loan record is associated with one book and one member. A loan may have a fine if the book is returned late.
- Members can register for multiple library events, and each event can have multiple speakers. Each event is assigned to one room.

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
[Sashtitha_ER3-1.pdf](https://github.com/user-attachments/files/33960691/Sashtitha_ER3-1.pdf)

![ER Diagram](er_diagram_restaurant.png)

### Entities and Attributes

| Entity | Attributes (PK, FK) | Notes |
|---|---|---|
| CUSTOMER | Customer_ID (PK), Name, Phone, Email | Stores customer details |
| RESERVATION | Reservation_ID (PK), Reservation_Date, Reservation_Time, No_of_Guests, Reservation_Type, Customer_ID (FK), Table_ID (FK), Waiter_ID (FK) | Stores reservation and walk-in details |
| RESTAURANT_TABLE | Table_ID (PK), Table_Number, Capacity, Table_Status | Stores restaurant table details |
| WAITER | Waiter_ID (PK), Waiter_Name, Phone | Stores waiter details |
| FOOD_ORDER | Order_ID (PK), Order_Date, Order_Time, Order_Status, Reservation_ID (FK) | Stores food order details |
| ORDER_ITEM | Order_ID (PK, FK), Dish_ID (PK, FK), Quantity, Unit_Price | Stores dishes included in each order |
| DISH | Dish_ID (PK), Dish_Name, Price, Category_ID (FK) | Stores food item details |
| CATEGORY | Category_ID (PK), Category_Name | Starter, Main Course, Dessert |
| BILL | Bill_ID (PK), Food_Charge, Service_Charge, Total_Amount, Bill_Date, Payment_Status, Reservation_ID (FK) | Stores billing details |
### Relationships and Constraints

| Relationship | Cardinality | Participation | Notes |
|---|---|---|---|
| CUSTOMER – RESERVATION (Makes) | 1:N | CUSTOMER: Partial; RESERVATION: Total | A customer can make multiple reservations |
| RESERVATION – RESTAURANT_TABLE (Assigned To) | N:1 | RESERVATION: Total; RESTAURANT_TABLE: Partial | Each reservation is assigned to one table |
| RESERVATION – FOOD_ORDER (Places) | 1:N | RESERVATION: Partial; FOOD_ORDER: Total | A reservation can have multiple food orders |
| FOOD_ORDER – ORDER_ITEM (Contains) | 1:N | FOOD_ORDER: Total; ORDER_ITEM: Total | Each order contains one or more order items |
| ORDER_ITEM – DISH (Includes) | N:1 | ORDER_ITEM: Total; DISH: Partial | Each order item refers to one dish |
| CATEGORY – DISH (Belongs To) | 1:N | CATEGORY: Partial; DISH: Total | A category can contain multiple dishes |
| RESERVATION – BILL (Generates) | 1:0..1 | RESERVATION: Partial; BILL: Total | A reservation may generate one bill |
| WAITER – RESERVATION (Serves) | 1:N | WAITER: Partial; RESERVATION: Total | A waiter can serve multiple reservations |

### Assumptions
- Each customer, reservation, table, waiter, and food order has a unique ID.
- A customer can make multiple reservations, but each reservation is assigned to one restaurant table and one waiter.
- Each food order contains one or more items, and a reservation may generate one bill.

---

## Instructions for Students

1. Complete **all three scenarios** (A, B, C).  
2. Identify entities, relationships, and attributes for each.  
3. Draw ER diagrams using **draw.io / diagrams.net** or hand-drawn & scanned.  
4. Fill in all tables and assumptions for each scenario.  
5. Export the completed Markdown (with diagrams) as **a single PDF**
