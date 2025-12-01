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
<img width="988" height="625" alt="image" src="https://github.com/user-attachments/assets/e970c332-9d69-4c66-839c-59c25142c719" />


### Entities and Attributes

| Entity | Attributes (PK, FK) | Notes |
|--------|--------------------|-------|
| Member | member_id (PK), name, gender, dob, email                    | Represents gym members who register for programs.     |
| Program | program_id (PK), program_name, fee, duration, schedule                   |Represents the different fitness programs (e.g., Yoga, Zumba, Weight Training).       |
| Trainers | trainer_id (PK), trainer_name, trainer_gender, trainer_phone, trainer_email, expertise                   | Stores trainer information (e.g., contact details, expertise).      |
| Sessions |session_id (PK), date, time, trainer_id (FK), program_id (FK)                    |Represents individual time-bound classes.       |
| Payment | payment_id (PK), amount, payment_type, payment_date, member_id (FK), program_id (FK)                  | Records payments made by members for specific programs.      |
|Attendance|attendance_id (PK), status, session_id (FK), trainer_id (FK)|Tracks attendance of members in specific sessions.|


### Relationships and Constraints

| Relationship | Cardinality | Participation | Notes |
|--------------|------------|---------------|-------|
|  enrolls_in           |    M:N        | Member (Total), Program (Partial)              |  A member can enroll in multiple programs; a program can have many members.     |
|   leads           |   1:M         |Program (Total), Trainer (Partial)| Each program is led by one trainer, but a trainer may lead multiple programs.      |
|   registers           |  M:N          |  Both Partial             | A member can register for many sessions, and each session can have many members.      |
|   includes           |  1:M          |   Program (Total), Session (Total)            | A program includes multiple sessions, but each session belongs to only one program.      |
|   has           | 1:M           | Program (Total), Payment (Total)              |A program can have many payments; each payment belongs to one program.       |
|tracks|1:M|Payment (Total), Session (Partial)|Payments are linked to sessions attended by members.|

### Assumptions
- A member must enroll in at least one program.
- A program must be led by at least one trainer.
- Payments are tied to members and programs (not to trainers directly).

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
<img width="988" height="812" alt="image" src="https://github.com/user-attachments/assets/a1518c6e-c6d8-46b3-99bb-56096482483a" />


### Entities and Attributes

| Entity | Attributes (PK, FK) | Notes |
|--------|--------------------|-------|
| Member       |  member_id (PK), name, phone_no, address, email                  | Represents people who are part of the library.      |
| Book       | book_id (PK), title, author, category, duedate                   | Represents books in the library.      |
|Overdue_Fine        | fine_id (PK), amount, member_id (FK)                   | Stores fines for books that were returned late.      |
|  Event      | event_id (PK), event_name, date, time                   | Represents library-organized events (workshops, talks, seminars).      |
| Speaker       |  speaker_id (PK), name, expertise                  | Represents external or internal experts invited for events.      |



### Relationships and Constraints

| Relationship | Cardinality | Participation | Notes |
|--------------|------------|---------------|-------|
|  borrows            |  M:N          | Both Total              | A member can borrow many books, and each book can be borrowed by many members (over time).      |
|   pays           |  1:M          |  Member (Partial), Fine (Total)             | A member may pay many fines; each fine belongs to one member.      |
|   loans           |   1:M         |  Book (Partial), Fine (Total)             | A book may be linked to fines when overdue.      |
| has             |      M:N      |      Both Total         | A book can be stored in multiple rooms, and a room can store multiple books.      |
|   books           |   1:M         | Room (Total), Event (Partial)              | A room can host multiple events, but each event is held in exactly one room.      |


### Assumptions
- A member must exist before borrowing books or registering for events.
- A book may or may not be borrowed; not all books will always have loans.
- Fines are only generated if a book is returned late.


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

<img width="881" height="832" alt="image" src="https://github.com/user-attachments/assets/67dde6da-824a-4593-8a6c-e2d1b48d9cbf" />


### Entities and Attributes
| Entity | Attributes (PK, FK) | Notes |
|--------|--------------------|-------|
| Customer       | customer_id (PK), name, phone_no, email, address                   | Stores customer information.      |
| Reservation       | reservation_id (PK), date, no_of_guests, customer_id (FK), restaurant_id (FK)                   | Records table bookings.      |
| Restaurant       | restaurant_id (PK), name, location, cuisine_type                   |Represents restaurants in the system.       |
| Order       |order_id (PK), order_date, total_amount, customer_id (FK), restaurant_id (FK)                    | Represents food orders made by customers.      |
| Delivery       |delivery_id (PK), delivery_date, delivery_status, order_id (FK)                    | Tracks delivery of placed orders.      |


### Relationships and Constraints

| Relationship | Cardinality | Participation | Notes |
|--------------|------------|---------------|-------|
|   have           |    1:M        |  Customer (Partial), Reservation (Total)             |  A customer can make many reservations, but each reservation is linked to exactly one customer.     |
|  place            |   1:M         |  Customer (Partial), Order (Total)             |A customer can place many orders; each order belongs to exactly one customer.       |
| receive             |   M:1         | Order (Total), Restaurant (Partial)              | Each order is received by exactly one restaurant, while a restaurant can receive many orders.      |
|   have           |   M:1         |  Reservation (Total), Restaurant (Partial)             | Each reservation is made at exactly one restaurant, while a restaurant can have many reservations.      |
|  associated_with            |  1:1          |  Both Total             |  Each order is associated with exactly one delivery record, and each delivery belongs to one order.     |


### Assumptions
- A customer may exist without making a reservation or placing an order.
- A reservation must be tied to both a customer and a restaurant.
- Every order must belong to a customer and a restaurant.

---

## Instructions for Students

1. Complete **all three scenarios** (A, B, C).  
2. Identify entities, relationships, and attributes for each.  
3. Draw ER diagrams using **draw.io / diagrams.net** or hand-drawn & scanned.  
4. Fill in all tables and assumptions for each scenario.  
5. Export the completed Markdown (with diagrams) as **a single PDF**
