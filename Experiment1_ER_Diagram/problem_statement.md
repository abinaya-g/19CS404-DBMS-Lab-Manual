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
<img width="743" height="692" alt="image" src="https://github.com/user-attachments/assets/b4080ffc-10ff-4391-ad41-0e6ad602fd78" />


### Entities and Attributes

| Entity | Attributes (PK, FK) | Notes |
|--------|--------------------|-------|
| PROGRAM | program_id (PK), program_name, schedule | Fitness programs offered by the gym |
| TRAINER | trainer_id (PK), trainer_name, specialization | Trainers responsible for conducting sessions |
| MEMBER | member_id (PK), name, membership_type, start_date | Registered gym members |
| SESSION | session_id (PK), session_date, time | Training sessions conducted by trainers |
| PAYMENT | payment_id (PK), amount, payment_date, payment_type | Payments made by members for memberships or sessions |

### Relationships and Constraints

| Relationship | Cardinality | Participation | Notes |
|--------------|------------|---------------|-------|
| MEMBER JOINS PROGRAM | M : N | Partial | Members can join multiple programs |
| PROGRAM ASSIGNED_TO TRAINER | M : N | Partial | A program may have multiple trainers |
| TRAINER CONDUCTS SESSION | 1 : N | Total (Session) | One trainer conducts multiple sessions |
| MEMBER ATTENDS SESSION | 1 : N | Partial | Members attend training sessions |
| MEMBER MAKES PAYMENT | 1 : N | Partial | Members can make multiple payments |

### Assumptions
- A member must be registered before joining programs or attending sessions.  
- A program can have multiple trainers assigned to it.  
- Each session is conducted by one trainer.  
- Members can attend multiple training sessions.  
- Payments are recorded for memberships and additional sessions.

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
<img width="799" height="688" alt="image" src="https://github.com/user-attachments/assets/f0dab54c-484f-4d4d-ba4c-5a57139b48d2" />


### Entities and Attributes

| Entity | Attributes (PK, FK) | Notes |
|--------|--------------------|-------|
| MEMBER | id (PK), name, phone, email | Represents a registered library member |
| BOOK | book_id (PK), title, author, category | Stores details of books available in the library |
| EVENT | event_id (PK), event_name, date, time | Library events such as talks or workshops |
| SPEAKER | speaker_id (PK), speaker_name, bio | Speakers or authors invited for events |
| ROOM | room_id (PK), room_name, capacity, room_type | Rooms used for events or study sessions |

### Relationships and Constraints

| Relationship | Cardinality | Participation | Notes |
|--------------|------------|---------------|-------|
| MEMBER BORROWS BOOK | 1 : N | Partial | A member can borrow multiple books |
| MEMBER REGISTERS EVENT | M : N | Partial | Members can register for multiple events |
| EVENT HAS SPEAKER | M : N | Total (Event) | Each event may have multiple speakers |
| EVENT USES ROOM | 1 : N | Total (Event) | Each event uses one room |
| ROOM USED_BY EVENT | 1 : N | Partial | A room can be used for multiple events |

### Assumptions
- Members must be registered before borrowing books.  
- A member can borrow multiple books over time.  
- Members can register for multiple events.  
- Events may feature multiple speakers or authors.  
- Each event takes place in one room.  
- Rooms can host multiple events at different times.

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
<img width="1181" height="839" alt="rest_dbms_anisha drawio" src="https://github.com/user-attachments/assets/28112f57-2ab9-43c8-a76a-7e84ec1978b4" />


### Entities and Attributes

| Entity | Attributes (PK, FK) | Notes |
|--------|--------------------|-------|
| Customer | CustomerID (PK), Name, Phone, Email | Stores customer details for reservations and contact |
| Reservation | ReservationID (PK), Date, Time, GuestCount, CustomerID (FK) | Represents a booking made by a customer |
| Table | TableID (PK), TableNumber, Capacity | Stores information about tables available in the restaurant |
| Waiter | WaiterID (PK), WaiterName, Phone | Waiter assigned to serve reservations |
| Order | OrderID (PK), OrderTime, OrderStatus, ReservationID (FK) | Food orders placed for a reservation |
| Dish | DishID (PK), DishName, Price, CategoryID (FK) | Menu items available for ordering |
| Category | CategoryID (PK), CategoryName | Groups dishes (Starter, Main Course, Dessert) |
| Bill | BillID (PK), TotalAmount, ServiceCharge, ReservationID (FK) | Billing details generated for each reservation |

### Relationships and Constraints

| Relationship | Cardinality | Participation | Notes |
|--------------|------------|---------------|-------|
| Customer makes Reservation | 1 : N | Partial | One customer can make many reservations |
| Reservation assigned_to Table | N : 1 | Total (Reservation) | Each reservation is assigned exactly one table |
| Reservation served_by Waiter | N : 1 | Total (Reservation) | A waiter can serve multiple reservations |
| Reservation places Order | 1 : N | Partial | A reservation can place multiple orders |
| Order contains Dish | M : N | Partial | An order may include multiple dishes |
| Dish belongs_to Category | N : 1 | Total (Dish) | Each dish belongs to exactly one category |
| Reservation generates Bill | 1 : 1 | Total | Every reservation produces one bill |

### Assumptions
- A customer must exist in the system before making a reservation.  
- Each reservation is assigned to only one table.  
- A waiter can serve multiple reservations at the same time.  
- A reservation may place multiple food orders during the dining session.  
- Each order can contain multiple dishes.  
- Each dish belongs to exactly one category (Starter, Main Course, Dessert).  
- Each reservation generates exactly one bill.  
- Service charge is included in the bill along with the total food amount.

---
## Instructions for Students

1. Complete **all three scenarios** (A, B, C).  
2. Identify entities, relationships, and attributes for each.  
3. Draw ER diagrams using **draw.io / diagrams.net** or hand-drawn & scanned.  
4. Fill in all tables and assumptions for each scenario.  
5. Export the completed Markdown (with diagrams) as **a single PDF**
