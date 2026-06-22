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


<img width="1128" height="717" alt="image" src="https://github.com/user-attachments/assets/0c741153-754d-4a88-a0ca-31b88ef2dfb6" />


### Entities and Attributes

| Entity  | Attributes (PK, FK) | Notes |
|----------|----------------------|-------|
| Member | MemberID (PK), Name, MembershipType, StartDate | Stores gym members’ details |
| Program | ProgramID (PK), ProgramName, Type | Yoga, Zumba, Weight Training, etc. |
| Trainer | TrainerID (PK), Name, Specialization | Each trainer may handle multiple programs |
| Session | SessionID (PK), Date, Time, TrainerID (FK), ProgramID (FK) | Personal training or group sessions |
| Payment | PaymentID (PK), MemberID (FK), Amount, PaymentDate, Type | Tracks membership & session payments |

---

### Relationships and Constraints

| Relationship | Cardinality | Participation | Notes |
|--------------|-------------|---------------|-------|
| Registers (Member–Program) | M:N | Partial (not all members join all programs) | A member may join many programs |
| AssignedTo (Trainer–Program) | M:N | Total for Program | Programs must have at least one trainer |
| Books (Member–Trainer–Session) | M:N | Partial | Members may book multiple trainers; sessions linked |
| Attends (Member–Session) | M:N | Partial | Records attendance |
| PaysFor (Member–Payment) | 1:M | Total for Payment | Each payment belongs to one member |
| Covers (Payment–Session) | 1:M | Optional | A payment can cover membership fee or session fee |

### Assumptions

- A member can enroll in multiple fitness programs.
- Trainers can conduct sessions for different programs.
- Payments may be made for memberships or personal sessions.
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

<img width="982" height="702" alt="image" src="https://github.com/user-attachments/assets/032d0acc-38ef-4b31-a601-8f80c4efeaab" />

### Entities and Attributes

| Entity | Attributes (PK, FK) | Notes |
|--------|----------------------|-------|
| Member | MemberID (PK), Name, Email, Phone | Library members |
| Book | BookID (PK), Title, Author, Category | Books available in the library |
| Loan | LoanID (PK), MemberID (FK), BookID (FK), LoanDate, ReturnDate, Fine | Tracks lending/return of books |
| Event | EventID (PK), Title, Date, RoomID (FK) | Library cultural events |
| Speaker | SpeakerID (PK), Name, Topic | Guest speakers/authors for events |
| Room | RoomID (PK), RoomName, Capacity | Rooms for events and study |
| Registration | RegID (PK), EventID (FK), MemberID (FK) | Members registering for events |

### Relationships and Constraints

| Relationship | Entities | Cardinality | Participation | Notes |
|--------------|----------|-------------|---------------|-------|
| Borrows | Member ↔ Book (via Loan) | M:N | Total on Loan | A member can borrow many books; tracked with dates |
| RegistersFor | Member ↔ Event (via Registration) | M:N | Total on Registration | Members can register for multiple events |
| HostedIn | Event ↔ Room | M:1 | Total on Event | Each event must be held in one room |
| HasSpeaker | Event ↔ Speaker | M:N | Partial | Events may have multiple speakers |
| FineApplied | Loan ↔ Member | 1:M | Partial | Overdue fines applied to member if late return |

---

### Assumptions

1.Each member, book, event, speaker, and room has a unique ID.

2.A member can borrow multiple books, but a book can be issued to only one member at a time.

3.Loan date and return date are recorded for every borrowed book.

4.Fine is calculated based on the number of overdue days.

5.A member can register for multiple events.

6.An event can have multiple speakers/authors.

7.A room can be booked for events or study, but only one booking per time slot.

8.A book belongs to only one category.


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

<img width="1311" height="902" alt="image" src="https://github.com/user-attachments/assets/6261c81a-6be2-44f7-854e-d1df7a3ecd06" />


### Entities and Attributes

| Entity | Attributes (PK, FK) | Notes |

| Entity | Attributes (PK, FK) | Notes |
|--------|----------------------|-------|
| Customer | CustomerID (PK), Name, Phone, Email | Restaurant customers |
| Reservation | ResID (PK), CustomerID (FK), Date, Time, Guests, TableID (FK) | Reservations or walk-ins |
| Table | TableID (PK), Capacity | Physical tables available |
| Order | OrderID (PK), ResID (FK), OrderTime | Orders linked to reservations |
| Dish | DishID (PK), Name, Category, Price | Menu items (starter, main, dessert) |
| OrderItem | OrderItemID (PK), OrderID (FK), DishID (FK), Quantity | Tracks multiple dishes per order |
| Bill | BillID (PK), ResID (FK), TotalAmount, ServiceCharge, Date | Bill generated per reservation |
| Waiter | WaiterID (PK), Name, Shift | Waiters assigned to reservations |

### Relationships and Constraints


| Relationship | Entities | Cardinality | Participation | Notes |
|--------------|----------|-------------|---------------|-------|
| Makes | Customer ↔ Reservation | 1:M | Total on Reservation | Customer can have multiple reservations |
| AssignedTo | Reservation ↔ Table | M:1 | Total on Reservation | Each reservation linked to one table |
| Places | Reservation ↔ Order | 1:M | Total on Order | A reservation can have multiple orders |
| Contains | Order ↔ Dish (via OrderItem) | M:N | Total on OrderItem | Orders can contain multiple dishes |
| Generates | Reservation ↔ Bill | 1:1 | Total on Bill | Each reservation produces one bill |
| ServedBy | Reservation ↔ Waiter | M:N | Partial | A reservation can be served by multiple waiters |

---

### Assumptions

1.Each customer, reservation, waiter, dish, and bill has a unique ID.

2.A reservation is made for a specific date and time with a fixed number of guests.

3.Walk-in customers are also recorded as reservations.

4.One reservation is assigned to one waiter, but a waiter can handle multiple reservations.

5.Each order is linked to one reservation.

6.An order can contain multiple dishes, and each dish belongs to one category.

7.Only one final bill is generated per reservation.

8.The bill includes food charges + service charges.


### RESULT

Thus the ER Diagram for each scenario has been drawn and explained successfully.
