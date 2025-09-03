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

<img width="1177" height="439" alt="image" src="https://github.com/user-attachments/assets/88451832-4072-4028-b0af-46b90e0c9da0" />


### **Entities and Attributes**

| Entity                          | Attributes (PK, FK)                                                                          | Notes                                                               |
| ------------------------------- | -------------------------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| **Trainer**                     | trainer\_id **(PK)**, name, specification                                                    | Specification includes yoga, zumba, weight training (multi-valued). |
| **Member**                      | member\_id **(PK)**, start\_date, membership                                                 | Each member has a unique ID and membership type.                    |
| **Training**                    | training\_id **(PK)**, trainer\_id **(FK)**, member\_id **(FK)**                             | Resolves many-to-many between Trainer and Member.                   |
| **Personal\_Training\_Session** | session\_id **(PK)**, timing, trainer\_id **(FK)**, member\_id **(FK)**                      | Represents individual training sessions.                            |
| **Attendance**                  | attendance\_id **(PK)**, member\_id **(FK)**, date, entry\_timing, exit\_timing, attendance% | Tracks attendance of members in sessions.                           |
| **Payment**                     | payment\_id **(PK)**, member\_id **(FK)**, payment\_method, type                             | Payment methods include cash, UPI, card, EMI.                       |
| **Enrollment\_Fee**             | fee\_id **(PK)**, member\_id **(FK)**, amount, date                                          | Captures fee paid by members.                                       |

---

### **Relationships and Constraints**

| Relationship                               | Cardinality                                   | Participation                                                   |
| ------------------------------------------ | --------------------------------------------- | --------------------------------------------------------------- |
| **Register** (Trainer–Member via Training) | Trainer (1..N), Member (1..N)                 | Total participation for Member and Trainer (must register).     |
| **Personal Training Session - Register**   | One session belongs to 1 trainer and 1 member | Total participation.                                            |
| **Enrollment Fee - Member**                | 1 Member : 1 Enrollment Fee                   | Mandatory participation (each member pays fee).                 |
| **Payment - Member**                       | 1 Member : N Payments                         | Optional participation (member may pay multiple times).         |
| **Attendance - Register**                  | 1 Register : N Attendance records             | Total participation (attendance is tied to registered members). |


### **Assumptions**

* Each **member** can register with multiple **trainers**, and each **trainer** can handle multiple members (many-to-many resolved via Training entity).
* Each member must pay an **enrollment fee** once at the start.
* **Payment methods** can be either online (UPI, Card, EMI) or cash, only one chosen per transaction.
* **Attendance** is recorded per session per member, including entry and exit times.
* Specifications for trainers are limited to **Yoga, Weight Training, Zumba** as per ER diagram.

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

<img width="1242" height="786" alt="image" src="https://github.com/user-attachments/assets/4991f81c-0d9e-4663-b7be-452f92192028" />


## **Entities and Attributes**

| Entity                               | Attributes (PK, FK)                                                                               | Notes                                                                |
| ------------------------------------ | ------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------- |
| **Books**                            | book\_id **(PK)**, title, author, price, available, publisher\_id **(FK)**                        | Each book is uniquely identified by `book_id`. Linked to publisher.  |
| **Publisher**                        | publisher\_id **(PK)**, name, address                                                             | Each publisher publishes many books.                                 |
| **Member**                           | member\_id **(PK)**, name, member\_type, expiry\_date                                             | Each member has unique ID and membership type.                       |
| **Borrowed** (Relationship as table) | borrow\_id **(PK)**, book\_id **(FK)**, member\_id **(FK)**, issue\_date, due\_date, return\_date | Resolves many-to-many between Books and Members (borrowing records). |


## **Relationships and Constraints**

| Relationship                       | Cardinality                                        | Participation                                                                   |
| ---------------------------------- | -------------------------------------------------- | ------------------------------------------------------------------------------- |
| **Published by** (Books–Publisher) | 1 Publisher : N Books                              | Total participation for Books (every book must have publisher).                 |
| **Borrowed by** (Books–Member)     | 1 Member : N Books, 1 Book : N Members (over time) | Partial participation (not all books must be borrowed, not all members borrow). |


## **Assumptions**

* Each book is published by **exactly one publisher**.
* A book can be borrowed **multiple times** by different members, but only one member at a time.
* The **Borrowed** relationship stores borrowing details (`issue_date`, `due_date`, `return_date`).
* The **availability** attribute in Books indicates whether the book is currently available.
* Members have **expiry dates** for their membership, after which they cannot borrow books.


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

<img width="1801" height="382" alt="image" src="https://github.com/user-attachments/assets/281bfbeb-2d95-410b-8c84-0c1ceceb27f3" />


## **Entities and Attributes**

| Entity          | Attributes (PK, FK)                                                         | Notes                                             |
| --------------- | --------------------------------------------------------------------------- | ------------------------------------------------- |
| **Waiter**      | waiter\_id **(PK)**, name, contact                                          | Each waiter has unique ID.                        |
| **Customer**    | customer\_id **(PK)**, name, phone                                          | Customers make reservations and orders.           |
| **Reservation** | reservation\_id **(PK)**, customer\_id **(FK)**, date, time, no\_of\_guests | Links customers to tables.                        |
| **Table**       | table\_id **(PK)**, table\_no, capacity                                     | Represents restaurant tables with capacity.       |
| **Bill**        | bill\_id **(PK)**, table\_id **(FK)**, total\_amount                        | Bill is generated per table per reservation/meal. |


## **Relationships and Constraints**

| Relationship                                         | Cardinality                         | Participation                                                  |
| ---------------------------------------------------- | ----------------------------------- | -------------------------------------------------------------- |
| **Order Dish** (Waiter–Customer)                     | Waiter (1..N), Customer (0..N)      | Partial (not all waiters must serve, not all customers order). |
| **Seat Reservation for Food** (Customer–Reservation) | Customer (1..N), Reservation (0..N) | Total for Customer (a customer must reserve to dine).          |
| **Booking** (Reservation–Table)                      | Reservation (1..1), Table (1..N)    | Total participation (reservation must be linked to a table).   |
| **Text Consumed** (Table–Bill)                       | Table (1..1), Bill (1..N)           | Total participation (every bill linked to a table).            |


## **Assumptions**

* Each **waiter** can serve multiple customers, but one customer is typically assigned to one waiter at a time.
* A **customer** can make multiple **reservations**.
* Each **reservation** is linked to **exactly one table**.
* Each **table** may generate multiple bills over time (different customers/reservations).
* **Bill amount** is calculated based on the food ordered and table consumed.
