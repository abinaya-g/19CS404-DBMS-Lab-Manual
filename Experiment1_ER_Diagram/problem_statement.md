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

<img width="1126" height="532" alt="image" src="https://github.com/user-attachments/assets/6dd67093-f638-4e03-a7a5-56b7975b1d28" />


### Entities and Attributes

| Entity | Attributes |
|--------|--------------------|
| Member  | Name,MemberID,PhoneNo,Membership Type,Starting Date,Ending Date|
|Program| ProgramID, Program Name |
|Trainer|TrainerID , Name,Phone No,Specialization|
|Session|Session ID,Member ID,Fee,TrainerID,Duration|
|Attendance| AttendanceID,SessionID,MemberID,Status,Date|
|Payment|PaymentID,MemberID,Amount,Payment Date,Payment Type|

### Relationships and Constraints

| Relationship | Cardinality | Participation | Notes |
|--------------|------------|---------------|-------|
|Member-Payment|1:N|Partial|A member can make multiple payments; each payment belongs to one member.|
|Member → Program|N:M|Partial |A member can join many programmes; a programme may include many members.|
|Trainer → Program|1:N|Partial | Each trainer conducts multiple programmes, but every programme is handled by one trainer.|
|Member/Trainer → Session | N:M | Partial | Sessions are attended by multiple members and managed by multiple trainers.|
### Assumptions
- The fitness club assumes that all member information provided during registration is accurate and updated.
- The club assumes that sufficient trainers, equipment, and facilities are always available for scheduled activities.
- The system assumes that staff have continuous access to the management software and required technology.

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

<img width="527" height="293" alt="image" src="https://github.com/user-attachments/assets/37eb7c14-a797-4c6b-93e9-0dfea429c425" />


### Entities and Attributes

| Entity | Attributes |
|--------|--------------------|
|Room Booking|BookingID,Date,RoomID,MemberID|
|Room|RoomID,Room Name,Type,Capacity|
|Member|Name,Membership Date,Phone No,MemberID|
|Event Registration |MemberID,EventID,Reg_ID|
|Event|EventID,Date,Name|
|Loan|Loan_date,DueDate,Return Date,LoanID|
|Book|BookID,Title,Author|

### Relationships and Constraints

| Relationship | Cardinality | Participation | Notes |
|--------------|------------|---------------|-------|
|Member → Loan|1:N|Partial|A member can receive many loans; each loan is issued to one member.|
|Event → Room|M:N|Partial|An event can be held in multiple rooms; each room can host multiple events.|
|Member → Event|M:N|Partial|A member can register for multiple events; an event can have many members.|
|Author → Event|M:N|Partial|Speakers or authors can join multiple events; each event can feature many speakers. 

### Assumptions
- The library assumes that members provide valid and accurate personal details during registration.
- The system assumes that all books, event resources, and facilities are properly catalogued and available as recorded.
- The library assumes that users return borrowed books on or before the due date to maintain smooth lending operations.

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

<img width="529" height="344" alt="image" src="https://github.com/user-attachments/assets/1d361208-02a6-42b9-b154-2c7950f3ca28" />


### Entities and Attributes

| Entity | Attributes|
|--------|--------------------|
|Customers|CustomerID,Phone No,Email,Name|
|Reservation|ReservationID,No_Of_Guest,Time,Date|
|Bill|Bill_ID,Amount|
|Order|Time,Date,OrderID|
|Dish|Dish_ID,Name,Price|
|Category|Category_ID,Name|
|Waiters|Name,Phone No,Waiter ID|
|Table|Table No,Capacity,Table_ID|

### Relationships and Constraints

| Relationship | Cardinality | Participation | Notes |
|--------------|------------|---------------|-------|
|Customer → Reservation|1:N|Partial|Each customer can make many reservations, and each reservation belongs to one customer.|
|Reservation → Table|1:N|Partial|A reservation may include one or more tables; each table may be reserved multiple times.|
|Category → Dish|1:N|Partial|A category can contain many dishes; each dish belongs to one category.|
|Reservation → Bill|1:1|Partial|Every reservation generates one bill.|

### Assumptions
- The restaurant assumes customers provide valid and accurate details when making reservations.
- The system assumes that tables, staff, and menu items are available as displayed during booking and ordering.
- The restaurant assumes customers will arrive on time and follow reservation and ordering policies.

---

## RESULT : 

The combined ER diagram effectively represents entities and relationships of the restaurant, fitness club, and library systems. It clearly captures interactions like reservations, sessions, and book lending, ensuring smooth data flow and efficient system management.
