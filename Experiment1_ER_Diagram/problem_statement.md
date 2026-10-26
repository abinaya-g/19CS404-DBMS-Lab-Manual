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
![AdithyaSivakumar_ERWorkshop (2)_page-0001](https://github.com/user-attachments/assets/81c63d5c-562d-4c36-85e1-612bdc8f3a04)


## Entities and Attributes

| Entity | Attributes (PK, FK) | Notes |
|--------|--------------------|-------|
| **Member** | **Member_ID (PK)**, Name, Membership_Type, Start_Date | Stores information about each club member. |
| **Program** | **Program_ID (PK)**, Program_Name, Program_Type, Duration | Represents various fitness programs available. |
| **Trainer** | **Trainer_ID (PK)**, Name, Specialty, Experience_Level | Holds details of all trainers. |
| **Enrollment** | **Member_ID (FK)**, **Program_ID (FK)** | Associates members with the programs they have enrolled in. |
| **Personal_Training_Session** | **Session_ID (PK)**, Date, Time, Fee, **Program_ID (FK)**, **Trainer_ID (FK)** | Represents a specific training session under a program, conducted by a trainer. |
| **Attendance** | **Attendance_ID (PK)**, Date, Status, **Session_ID (FK)** | Records attendance for each training session. |
| **Payment** | **Payment_ID (PK)**, Date, Amount, Payment_Type, **Member_ID (FK)** | Contains payment details for members. |

---

## Relationships and Constraints

| Relationship | Cardinality | Participation | Notes |
|--------------|-------------|---------------|-------|
| Member – Enrollment | 1 to N | Member (Mandatory), Enrollment (Dependent) | A member can enroll in multiple programs. |
| Program – Enrollment | 1 to N | Program (Mandatory), Enrollment (Dependent) | A program can have many enrolled members. |
| Program – Personal_Training_Session | 1 to N | Program (Mandatory), Session (Dependent) | Each program includes multiple training sessions. |
| Trainer – Personal_Training_Session | 1 to N | Trainer (Mandatory), Session (Dependent) | A trainer can conduct many training sessions. |
| Session – Attendance | 1 to N | Session (Mandatory), Attendance (Dependent) | Each session can have many attendance records. |
| Member – Payment | 1 to N | Member (Mandatory), Payment (Dependent) | Each member can make multiple payments. |

---

## Assumptions

- Each member can enroll in multiple programs, but an enrollment record must exist for participation.  
- Each program can have several sessions and be handled by multiple trainers over time.  
- Attendance is tracked per session, not per program.  
- Payment records are linked directly to members, not sessions or programs.  
- Trainer specialization helps assign them to suitable programs.  


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
![AdithyaSivakumar_ERWorkshop (2)_page-0002](https://github.com/user-attachments/assets/02d9087d-8dd2-434a-8c1e-d6b00f3f00cc)

## Entities and Attributes

| Entity | Attributes (PK, FK) | Notes |
|--------|--------------------|-------|
| **Member** | **Member_ID (PK)**, Name, Email, Membership_Type | Stores details of library members. |
| **Speaker** | **Speaker_ID (PK)**, Name, Bio | Represents guest speakers who participate in library events. |
| **Event** | **Event_ID (PK)**, Event_Name | Contains information about different library events. |
| **Room** | **Room_ID (PK)**, Room_Number | Represents rooms in the library where events are held. |
| **Books** | **Fine_ID (PK)**, Amount, Date, **Member_ID (FK)**, **Trainer_ID (FK)** | Tracks fines or book borrowing details for each member. |
| **Borrow** | **Member_ID (FK)**, **Speaker_ID (FK)** | Represents the borrowing relationship between members and speakers/authors. |
| **Register** | **Event_ID (FK)**, **Room_ID (FK)** | Associates events with rooms where they are conducted. |

---

## Relationships and Constraints

| Relationship | Cardinality | Participation | Notes |
|--------------|-------------|---------------|-------|
| Member – Borrow | 1 to N | Member (Mandatory), Borrow (Dependent) | A member can borrow multiple books or participate in several borrow actions. |
| Speaker – Borrow | 1 to N | Speaker (Mandatory), Borrow (Dependent) | A speaker (or author) can be associated with multiple borrow actions. |
| Event – Register | 1 to N | Event (Mandatory), Register (Dependent) | Each event can be registered in multiple rooms. |
| Room – Register | 1 to N | Room (Mandatory), Register (Dependent) | A room can host multiple events. |
| Member – Books | 1 to N | Member (Mandatory), Books (Dependent) | Each member can have multiple books or fines. |
| Speaker – Room | 1 to 1 | Speaker (Mandatory), Room (Dependent) | Each speaker uses one room for an event. |

---

## Assumptions

- Each member can borrow multiple books and participate in multiple events.  
- Each book record can include fine details related to a member’s borrowing.  
- Speakers are assigned to rooms to host or conduct events.  
- Each event must occur in at least one room.  
- Books table may also include information about issued fines for overdue returns.  


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

![AdithyaSivakumar_ERWorkshop (2)_page-0003](https://github.com/user-attachments/assets/74e8c383-998b-4dee-b7ba-8422bfc04b63)

### Entities and Attributes

| Entity | Attributes (PK, FK) | Notes |
|--------|--------------------|-------|
| **Customer** | **Customer_ID (PK)**, Name, Contact | Stores details of customers who make table reservations. |
| **Dish** | **Dish_ID (PK)**, Name, Category | Contains information about dishes available in the restaurant. |
| **Waiter** | **Waiter_ID (PK)**, Name | Represents waiters serving the restaurant. |
| **Reservation** | **Reservation_ID (PK)**, Date, Time, Num_Guests | Holds details about each reservation made by customers. |
| **Bills** | **Bill_ID (PK)**, Total_Charge | Contains billing information for each reservation. |

---

## Relationships and Constraints

| Relationship | Cardinality | Participation | Notes |
|--------------|-------------|---------------|-------|
| Customer – Reserves – Dish | N to N | Both optional | A customer can reserve multiple dishes, and each dish can be reserved by many customers. |
| Reservation – Contains – Waiter | N to N | Reservation (Dependent), Waiter (Mandatory) | A reservation can involve multiple waiters, and a waiter can serve many reservations. |
| Customer – Bills | 1 to N | Customer (Mandatory), Bills (Dependent) | Each customer can have multiple bills. |
| Reservation – Bills | 1 to N | Reservation (Mandatory), Bills (Dependent) | Each reservation results in one or more bills. |

---

## Assumptions

- A customer must exist before making a reservation.  
- A reservation may include multiple dishes and involve multiple waiters.  
- Each reservation generates a corresponding bill.  
- A waiter can serve multiple customers during different reservations.  
- Dish details are predefined in the menu database.  


## Instructions for Students

1. Complete **all three scenarios** (A, B, C).  
2. Identify entities, relationships, and attributes for each.  
3. Draw ER diagrams using **draw.io / diagrams.net** or hand-drawn & scanned.  
4. Fill in all tables and assumptions for each scenario.  
5. Export the completed Markdown (with diagrams) as **a single PDF**
