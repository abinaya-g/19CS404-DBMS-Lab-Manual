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
<img width="1092" height="902" alt="ER DIAGRAM A EXP 1" src="https://github.com/user-attachments/assets/cb6e9e26-66cb-4f9f-a76f-b097c9990726" />

*Paste or attach your diagram here*  
![ER Diagram](er_diagram_fitness.png)

### Entities and Attributes

| Entity | Attributes (PK, FK) | Notes |
|--------|--------------------|-------|
| Member | Member ID (PK), Name, Membership type, Start date | A person registered with the gym |
| Program | Program ID (PK), Program name, Duration | Yoga, Zumba, Weight training |
| Trainer | Trainer ID (PK), Trainer name, Specialization, Phone no | Conducts sessions and is assigned to programs |
| Training session | Session ID (PK), Session date, Session time, Member ID (FK), Trainer ID (FK) | A personal training session |
| Attendance | Attendance ID (PK), Attendance date, Status, Session ID (FK) | One record per session |
| Payment | Payment ID (PK), Amount, Payment type, Payment date, Member ID (FK) | Payment type separates membership and session payments |

### Relationships and Constraints

| Relationship | Cardinality | Participation | Notes |
|--------------|------------|---------------|-------|
| Member Makes Payment | 1:N | Member partial, Payment total | A member can make many payments |
| Member Joins Program | M:N | Both partial | Needs a Member_Program junction table |
| Trainer Assigned to Program | M:N | Both partial | Needs a Trainer_Program junction table |
| Member Books Training session | 1:N | Member partial, Session total | A session belongs to one member |
| Trainer Conducts Training session | 1:N | Trainer partial, Session total | A session has one trainer |
| Training session Has Attendance | 1:1 | Session partial, Attendance total | Attendance is recorded after the session |

### Assumptions
- Payment type shows whether a payment is for a membership or a session.
- A personal training session involves one member and one trainer.
- Attendance status is stored only in Attendance, not in Training session.
- Each M:N relationship becomes a junction table in the relational schema.

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
<img width="1290" height="907" alt="ER DIAGRAM B EXP 1" src="https://github.com/user-attachments/assets/97615ef2-b1ff-4eae-b1bc-41efb8b3e557" />

*Paste or attach your diagram here*  
![ER Diagram](er_diagram_library.png)

### Entities and Attributes

| Entity | Attributes (PK, FK) | Notes |
|--------|--------------------|-------|
| Book | Book ID (PK), Title, Author, Category | One row per book |
| Members | Member ID (PK), Member name, Email ID, Join date | Email ID is multivalued |
| Borrowing | Borrowing ID (PK), Lend date, Due date, Return date, Book ID (FK), Member ID (FK) | Return date stays empty until the book comes back |
| Fine | Fine ID (PK), Amount, Fine date, Payment status, Borrowing ID (FK) | Created only for late returns |
| Event | Event ID (PK), Event name, Event date, Event time, Venue | Cultural events run by the library |
| Speaker | Speaker ID (PK), Speaker name, Email ID, Phone no | Email ID and Phone no are multivalued |
| Room | Room ID (PK), Room name, Capacity | Rooms used for events and study |
| Booking | Booking ID (PK), Booking date, Start time, End time, Purpose, Room ID (FK), Member ID (FK), Event ID (FK, optional) | Event ID is empty for study bookings |

| Relationship | Cardinality | Participation | Notes |
|--------------|------------|---------------|-------|
| Book Has Borrowing | 1:N | Book partial, Borrowing total | A book is lent many times |
| Members Makes Borrowing | 1:N | Members partial, Borrowing total | A member can have many loans |
| Borrowing May generate Fine | 1:1 | Borrowing partial, Fine total | Only late returns get a fine |
| Members Register for Event | M:N | Both partial | Needs a Registration junction table |
| Event Has Speaker | M:N | Event total, Speaker partial | Needs an Event_Speaker junction table |
| Room Has Booking | 1:N | Room partial, Booking total | A booking is for one room |
| Booking Reserved for Event | N:1 | Both partial | Study bookings have no event |
| Members Made by Booking | 1:N | Members partial, Booking total | A member can make many bookings |


### Assumptions
- Due date is set when the book is issued, and a fine is created only if Return date is later than Due date.
- Booking date is the day the room is used, and Start time and End time give the hours.
- A room can't have two bookings with overlapping times on the same date.
- A member or speaker can have more than one Email ID or Phone no.
- Only registered members can borrow books, register for events or book rooms.

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
<img width="1852" height="762" alt="ER DIAGRAM C EXP 1" src="https://github.com/user-attachments/assets/38b99f06-cfaa-4a1c-b169-0c250128d2a1" />

*Paste or attach your diagram here*  
![ER Diagram](er_diagram_restaurant.png)

### Entities and Attributes

| Entity | Attributes (PK, FK) | Notes |
|--------|--------------------|-------|
| Customer | Customer ID (PK), Customer name, Phone no, Email ID | Phone no and Email ID are multivalued |
| Table | Table ID (PK), Location, Capacity | Table ID is also the number shown on the table |
| Waiter | Waiter ID (PK), Waiter name, Phone no, Shift | Phone no is multivalued |
| Reservation | Reservation ID (PK), Reservation types, Date, Time, Number of guests, Customer ID (FK), Table ID (FK), Waiter ID (FK) | Reservation types holds Advance or Walk-in |
| Order | Order ID (PK), Order time, Status, Reservation ID (FK) | Placed during a reservation |
| Dish | Dish ID (PK), Dish name, Price, Description, Category ID (FK) | Price is used to calculate Food charge |
| Category | Category ID (PK), Category name, Availability | Starter, main, dessert |
| Bill | Bill ID (PK), Food charge, Service charge, Reservation ID (FK) | One bill per reservation |

### Relationships and Constraints

| Relationship | Cardinality | Participation | Notes |
|--------------|------------|---------------|-------|
| Customer Makes Reservation | 1:N | Customer partial, Reservation total | A customer can make many reservations |
| Table Reserved Reservation | 1:N | Table partial, Reservation total | The same table is reserved at different times |
| Waiter Serves Reservation | 1:N | Waiter partial, Reservation total | Each reservation has one waiter |
| Reservation Has Order | 1:N | Reservation partial, Order total | A reservation can have several orders |
| Order Contains Dish | M:N | Order total, Dish partial | Needs an Order_Dish junction table with Quantity |
| Category Includes Dish | 1:N | Category partial, Dish total | Each dish belongs to one category |
| Reservation Generates Bill | 1:1 | Reservation partial, Bill total | A bill exists once the reservation is billed |


### Assumptions
- Walk-ins use the same Reservation entity with Reservation types set to Walk-in, and a customer record with at least a name is created for them.
- Bill total is Food charge plus Service charge, and Food charge is calculated from the Price of the ordered dishes.
- Quantity of each dish is stored in the Order_Dish junction table.
- A customer can have more than one Phone no or Email ID.
---

## Instructions for Students

1. Complete **all three scenarios** (A, B, C).  
2. Identify entities, relationships, and attributes for each.  
3. Draw ER diagrams using **draw.io / diagrams.net** or hand-drawn & scanned.  
4. Fill in all tables and assumptions for each scenario.  
5. Export the completed Markdown (with diagrams) as **a single PDF**
