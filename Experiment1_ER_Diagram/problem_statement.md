### Relationships and Constraints

JOIN – Connects MEMBERS and PROGRAM.
A member joins a program. This is generally a many-to-many relationship.
CONDUCTS – Connects PROGRAM and TRAINERS.
A trainer conducts a program. This is also typically many-to-many.
DUTY – Connects TRAINERS and PAYMENT.
Payments are linked to the duties of trainers. Normally a trainer can have many payments, but each payment refers to one trainer (one-to-many)


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

<img width="705" height="535" alt="image" src="https://github.com/user-attachments/assets/5932656a-7022-4a30-9c08-7bbb871d8237" />

### Entities and Attributes


Member
Attributes: MemberID, Name, Address, Phone, Email, MembershipDate.
Loan
Attributes: LoanID, LoanDate, ReturnDate, ActualReturnDate.
Book
Attributes: BookID, Title, Author, Category, Status.
Event
Attributes: EventID, EventName, EventDate, Description.
Speaker
Attributes: SpeakerID, Name, Biography.
Room
Attributes: RoomID, RoomName, Type, Capacity.
Registration
Attributes: RegistrationID, RegistrationDate.


### Relationships and Constraints

Member – Loan – Book
A member can borrow (loan) many books. A loan connects a member and a book.
Cardinality: Member 1..M — Loan M..1 — Book (a member can have many loans; a book can appear in many loans over time).
Member – Registration – Event
A member registers for an event. Registration acts as an associative entity containing RegistrationDate.
Cardinality: Many-to-Many through Registration.
Event – Speaker
An event can have many speakers and a speaker can speak at many events.
Cardinality: Many-to-Many.
Event – Room
An event takes place in a room. A room can host many events over time.
Cardinality: One-to-Many (one room can hold many events, each event occurs in one room).


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

<img width="754" height="453" alt="image" src="https://github.com/user-attachments/assets/c2bd1016-4843-439b-8661-ef5690ee3556" />

### Entities and Attributes

Customer
Attributes: CustomerID, Name, Phone.
Reservation
Attributes: ReservationID, Date, Time, GuestCount, CustomerID (FK).
Table
Attributes: TableID, Location, Capacity.
Waiter
Attributes: WaiterID, Name.
Bill
Attributes: PaymentID, Amount, ServiceCharge, Total, ReservationID (FK), CustomerID (FK).

### Relationships and Constraints

Customer – Reservation
A customer makes reservations.
Cardinality: One customer can make many reservations, but each reservation belongs to one customer (1:M).
Reservation – Table
Each reservation is assigned to a table.
Cardinality: One reservation is assigned to one table, and a table can host many reservations over time (1:N).
Reservation – Waiter
Each reservation is served by a waiter.
Cardinality: One reservation is served by one waiter, and a waiter can serve many reservations (1:N).
Reservation – Bill
Each reservation generates a bill.
Cardinality: One reservation generates exactly one bill, and each bill corresponds to one reservation (1:1).
Customer – Bill
A customer makes payments (bills).
Cardinality: One customer can have many bills, and each bill is linked to one customer (1:N).
