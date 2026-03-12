# ER Diagram Workshop – Submission Template

### NAME:SUSHMITHA S
### REG NO:212224230282

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

<img width="1203" height="827" alt="dbmsexp1 1" src="https://github.com/user-attachments/assets/7e5caa3d-8b50-4a09-8a1b-e3202d3eb02b" />


### Entities and Attributes

| Entity | Attributes (PK, FK) | Notes |
|--------|--------------------|-------|
|TRAINER |trainer_id (PK), name, specialization |The primary key ensures each trainer is unique|
|MEMBER  |member_id (PK), name, contact_number, start_date, membership_type |Added contact and date from the diagram|
|PROGRAM |program_id (PK), program_name, fees |Includes "Yoga, Zumba, etc." as instances of program_name|
|SESSION |session_id (PK), scheduled_time, trainer_id (FK)|trainer_id is a FK here because a Trainer "Leads" the session|
|PAYMENT |payment_id (PK), amount, payment_method, member_id (FK) |member_id links the payment to the person paying|

### Relationships and Constraints

| Relationship | Cardinality | Participation | Notes |
|--------------|------------|---------------|-------|
| Members ↔ Trainers | Many-to-Many (M:M)|Partial |Labeled as "Personal Training" in the diagram |
|Members ↔ Program  |Many-to-Many (M:M) |Partial|Labeled as "Joins" |
|Trainers ↔ Program|Many-to-Many (M:M) | Partial  |Labeled as "Trains"   |
|Trainers ↔ Session|One-to-Many (1:M)|Total (Session)|One trainer can lead many sessions; each session has one trainer.|
|Member ↔ Payment|One-to-Many (1:M)|Total (Payment)|A member can make many payments (e.g., monthly)|

### Assumptions
Each member and trainer has a unique ID.

A member can enroll in more than one fitness program.

A trainer can handle multiple sessions and programs.

Each session is conducted by one trainer and records attendance.

Each session generates one payment with a fixed amount.


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

<img width="1326" height="773" alt="dbmsexp1 2" src="https://github.com/user-attachments/assets/368cbca2-f303-4f70-ac14-23da60e2b068" />


### Entities and Attributes

| Entity | Attributes (PK, FK) | Notes |
|--------|--------------------|-------|
|Members| Member ID (PK), Name, Phone, Email |Unique identifier for each library member |
|Book  | Book ID (PK), Title, Author, Category |Unique identifier for each book in the collection   |
|Events | Event ID (PK), Event Name, Event Date, Room ID (FK)|Room ID is listed as an attribute, making it a Foreign Key from the Room entity.  |
|Speaker |Speaker ID (PK), Speaker Name, Contact Information  |Unique identifier for guest speakers. |
|Room  |Room ID (PK), Room Name, Capacity   |Unique identifier for the venue/location       |

### Relationships and Constraints


| Relationship | Cardinality | Participation | Notes |
|--------------|------------|---------------|-------|
|  Borrow  |  Many-to-Many (M:N) | Partial   |Members can borrow multiple books; includes attributes: Fine Amount, Return Date, and Due Date. |
|Register |Many-to-Many (M:N)   |Partial   |Many members can register for many events  |
|Booked     | One-to-Many (1:N)  | Total    | A room can be booked for multiple events, but each event is linked to one specific room.      |

### Assumptions
Each member, book, event, loan, speaker, and room has a unique ID.

A member can borrow multiple books, but a book is borrowed by one member at a time.

A loan record is created for each book borrowed, with loan and return dates.

A member can register for multiple events, and each event can have many members.

Each event is conducted in one room and can have multiple speakers.



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

 

![dbmsexp1 3](https://github.com/user-attachments/assets/81e742ed-dd9d-4ef1-a758-d99244ed71d8)


### Entities and Attributes

| Entity | Attributes (PK, FK) | Notes |
|--------|--------------------|-------|
|Customer | CustomerID (PK), Name, ContactInfo   |Represents the patrons of the restaurant.|
| Reservation | ReservationID (PK), Date, Time, NumberOfGuests, CustomerID (FK), TableID (FK) | Linked to a specific customer and an assigned table.      |
| Table |TableID (PK), Capacity, Status |Represents physical tables; status tracks availability|
|Order |OrderID (PK), CustomerID (FK)    | An order is placed by a customer; contains specific dish IDs   |
| Bill | BillID (PK), Amount, Service Charge, OrderID (FK)  | Generated based on the order details  |
|Dish|DishID (PK), Name, Price|The menu items available for order|
|Waiter|WaiterID (PK), Name|Staff members who provide service.|

### Relationships and Constraints

| Relationship | Cardinality | Participation | Notes |
|--------------|------------|---------------|-------|
| Makes  | 1:M (One-to-Many)  | Total (Reservation)  |One customer can make multiple reservations.  |
| Assigned to    | M:1 (Many-to-One)   | Total (Reservation)     |Multiple reservations can be assigned to one table (at different times).  |
|Generates    | 1:1 (One-to-One)     |  Total   |One order generates exactly one bill |
|Serves|M:M (Many-to-Many)|Partial|Waiters provide service to multiple service instances.|
|Orderitem|M:M (Many-to-Many)|Total|Connects orders to specific dishes and their quantities.|

### Assumptions
Each customer, order, reservation, table, waiter, and bill has a unique ID.

A customer can place multiple orders, but each order belongs to one customer.

A customer can make multiple reservations, and each reservation is for one table.

Each reservation is served by one waiter.

Each reservation generates one bill with a total amount.



## Instructions for Students

1. Complete **all three scenarios** (A, B, C).  
2. Identify entities, relationships, and attributes for each.  
3. Draw ER diagrams using **draw.io / diagrams.net** or hand-drawn & scanned.  
4. Fill in all tables and assumptions for each scenario.  
5. Export the completed Markdown (with diagrams) as **a single PDF**


