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

<img width="1536" height="1024" alt="ChatGPT Image Nov 21, 2025, 08_39_30 AM" src="https://github.com/user-attachments/assets/073c6205-a743-48ec-be18-beaa33ee5825" />

### Entities and Attributes

| Entity                     | Attributes (PK, FK)                                   | Notes                                                        |
|----------------------------|--------------------------------------------------------|-------------------------------------------------------------|
| Member                     | MemberID (PK), Name, MembershipType, StartDate        | Stores member details. Members can join programs & sessions. |
| Program                    | ProgramID (PK), ProgramName                           | Gym programs like Yoga, Zumba, Weight Training.              |
| Trainer                    | TrainerID (PK), TrainerName, Specialization           | Trainers assigned to programs and personal sessions.         |
| PersonalTrainingSession    | SessionID (PK), SessionDate, MemberID (FK), TrainerID (FK) | Personal 1-to-1 training bookings.                      |
| Attendance                 | AttendanceID (PK), Date, MemberID (FK), ProgramID (FK) | Tracks member attendance for programs.                      |
| Payment                    | PaymentID (PK), Amount, PaymentDate, MemberID (FK), SessionID (FK, optional) | Tracks membership & session payments. |

### Relationships and Constraints

| Relationship                    | Cardinality       | Participation        | Notes                                                           |
|---------------------------------|--------------------|-----------------------|------------------------------------------------------------------                       |
| Member — joins — Program        | Many–to–Many      | Total on Member, Partial on Program | A member can join multiple programs; a program may have many members.      |
| Trainer — assigned to — Program | Many–to–Many      | Partial on both       | A program can have multiple trainers; trainers may handle many programs.                 |
| Member — books — PersonalTrainingSession | One–to–Many | Total on Session, Partial on Member | Each session is for one member; a member can book many sessions.        |
| Trainer — conducts — PersonalTrainingSession | One–to–Many | Total on Session, Partial on Trainer | Each session is handled by one trainer; a trainer can conduct many.|
| Member — has — Attendance       | One–to–Many       | Total on Attendance   | Attendance entry must belong to a member.                                                |
| Program — recorded in — Attendance | One–to–Many   | Total on Attendance   | Attendance is always for a valid program.                                                 |
| Member — makes — Payment        | One–to–Many       | Total on Payment      | Every payment belongs to a specific member.                                              |
| PersonalTrainingSession — billed in — Payment | Optional (0..1) to Many | Partial on Payment | Payments may or may not be linked to sessions.                          |

### Assumptions

1. Each member, trainer, program, and session has a unique ID.
2. A member can join many programs; a program may have no members.
3. A trainer can handle multiple programs.
4. Personal training sessions always involve one member and one trainer.
5. Payments are always linked to a member; linking to a session is optional.
6. Attendance is recorded only for programs.
7. A program may exist even without trainers assigned.
8. Dates are stored in standard date formats.
9. Members can have multiple attendance records on different days.
10. Trainers can exist without conducting any sessions.


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

<img width="1536" height="1024" alt="ChatGPT Image Nov 21, 2025, 08_51_36 AM" src="https://github.com/user-attachments/assets/a2468007-7059-4a3d-b70d-292aedfa2290" />


### Entities and Attributes

| Entity          | Attributes (PK, FK)                                       | Notes                                                       |
|-----------------|------------------------------------------------------------|------------------------------------------------------------|
| Member          | MemberID (PK), Name, Email, Phone                          | Library members who borrow books and attend events.        |
| Book            | BookID (PK), Title, Author, Category                        | Each book has unique ID; used for lending.                |
| Loan            | LoanID (PK), LoanDate, ReturnDate, DueDate, MemberID (FK), BookID (FK) | Tracks book borrowing and returns.             |
| Event           | EventID (PK), EventName, EventDate, RoomID (FK)             | Events organized by the library.                          |
| Speaker         | SpeakerID (PK), SpeakerName, Expertise                       | Speakers/authors who participate in events.              |
| Room            | RoomID (PK), RoomName, Capacity                              | Rooms used for events or study booking.                  |
| MemberEventReg  | RegID (PK), MemberID (FK), EventID (FK)                      | Member registrations for events.                         |
| Fine            | FineID (PK), Amount, PaidStatus, LoanID (FK)                | Overdue fines for late book returns.                      |


### Relationships and Constraints

| Relationship                       | Cardinality       | Participation        | Notes                                                        |
|------------------------------------|--------------------|-----------------------|--------------------------------------------------------------|
| Member — borrows — Book (Loan)     | One–to–Many        | Total on Loan         | A member can borrow many books; each loan belongs to one member. |
| Book — issued in — Loan            | One–to–Many        | Total on Loan         | A book can have many loans over time.                       |
| Member — registers for — Event     | Many–to–Many       | Partial on both       | A member may register for multiple events.                  |
| Event — has — Speaker              | Many–to–Many       | Partial on both       | An event can have multiple speakers.                        |
| Event — uses — Room                | Many–to–One        | Total on Event        | Each event is conducted in one room.                        |
| Loan — generates — Fine            | One–to–One (0..1)  | Partial on Loan       | A fine exists only if the book is overdue.                  |


### Assumptions:

- Each book, member, event, and speaker has a unique ID.
- A book can only be borrowed by one member at a time.
- Fine is generated only when a loan exceeds the due date.
- A member can attend many events; an event may have no registrations.
- Each event is assigned to exactly one room.
- A speaker may participate in multiple events.
- ReturnDate may be NULL when book is not returned yet.

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

<img width="1024" height="1024" alt="ChatGPT Image Nov 21, 2025, 08_59_02 AM" src="https://github.com/user-attachments/assets/8bb68d09-d288-4033-ba0f-2a11b642edbb" />


### Entities and Attributes

| Entity        | Attributes (PK, FK)                                      | Notes                                      |
|---------------|-----------------------------------------------------------|---------------------------------------------|
| Customer      | CustomerID (PK), Name, Phone, Email                       | Customers who place orders and reservations |
| MenuItem      | ItemID (PK), ItemName, Price, Category                    | Food items available in the restaurant      |
| Order         | OrderID (PK), OrderDate, CustomerID (FK), TotalAmount     | Stores information about customer orders    |
| OrderItem     | OrderItemID (PK), OrderID (FK), ItemID (FK), Quantity     | Maps each item included in an order         |
| Reservation   | ReservationID (PK), CustomerID (FK), TableNo, Date, Time  | Stores customer table bookings              |
| Payment       | PaymentID (PK), OrderID (FK), AmountPaid, PaymentMethod   | Tracks payments for orders                  |

### Relationships and Constraints

| Relationship                     | Cardinality      | Participation         | Notes                                           |
|----------------------------------|------------------|------------------------|--------------------------------------------------|
| Customer — places — Order        | One-to-Many      | Total on Order         | A customer can place many orders                |
| Order — contains — OrderItem     | One-to-Many      | Total on OrderItem     | Each order has multiple ordered items           |
| MenuItem — appears in — OrderItem| One-to-Many      | Partial on MenuItem    | A menu item can appear in many orders           |
| Customer — makes — Reservation   | One-to-Many      | Partial on Customer    | Customers can reserve tables                    |
| Order — has — Payment            | One-to-One       | Partial on Payment     | Some orders may be pending without payment      |

### Assumptions
- Each customer, order, and menu item has a unique ID.
- A customer may place orders without making reservations.
- Payment is linked only to orders, not reservations.
- A reservation is always for a single table.
- Menu items can exist even if they are not ordered.

## Instructions for Students

1. Complete **all three scenarios** (A, B, C).  
2. Identify entities, relationships, and attributes for each.  
3. Draw ER diagrams using **draw.io / diagrams.net** or hand-drawn & scanned.  
4. Fill in all tables and assumptions for each scenario.  
5. Export the completed Markdown (with diagrams) as **a single PDF**
