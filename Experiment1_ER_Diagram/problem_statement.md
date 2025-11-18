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

 <img width="1126" height="756" alt="image" src="https://github.com/user-attachments/assets/d18b79ac-058e-4347-98cb-2c1831d69a10" />

### Entities and Attributes

| **Entity**          | **Attributes (PK, FK)**                                      | **Notes**                                        |
| ------------------- | ------------------------------------------------------------ | ------------------------------------------------ |
| **Member**          | Member_id (PK), Name, Contact_no, Membership_type (FK)       | Each member belongs to one membership type.      |
| **Membership_type** | Type_name (PK)                                               | Stores membership categories like Basic/Premium. |
| **Trainer**         | Trainer_id (PK), Name, Specialization                        | Trainers who conduct trainings.                  |
| **Training**        | Training_id (PK), Title, Date, Trainer_id (FK)               | A trainer conducts many trainings.               |
| **Attendance**      | Attendance_id (PK), Member_id (FK), Training_id (FK), Status | Shows whether a member attended a training.      |
| **Payment**         | Payment_id (PK), Member_id (FK), Amount, Date                | Members can make multiple payments.              |


### Relationships and Constraints

| **Relationship**                   | **Cardinality**                      | **Participation**                         | **Notes**                      |
| ---------------------------------- | ------------------------------------ | ----------------------------------------- | -------------------------------------------- |
| Member — Membership_type           | Many Members : 1 Membership_type     | Member (partial), Membership_type (total) | Each member must have one membership type.   |
| Member — Payment                   | 1 Member : Many Payments             | Member (total), Payment (partial)         | A member can make many payments.             |
| Trainer — Training                 | 1 Trainer : Many Trainings           | Trainer (partial), Training (partial)     | A trainer conducts multiple trainings.       |
| Member — Training (via Attendance) | Many Members : Many Trainings        | Both partial                              | Attendance table stores the link and status. |
| Training — Attendance              | 1 Training : Many Attendance records | Training (partial)                        | A training can have many attendees.          |


### Assumptions
- Training means a scheduled class (has a date and a trainer).

- Membership_type is a short lookup (like “Basic” or “Premium”) — stored by name.

- Attendance is used only to record if a member attended a specific training.

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

<img width="923" height="670" alt="image" src="https://github.com/user-attachments/assets/a63a351a-68ee-4e64-996e-f15c4d0c0912" />

### Entities and Attributes

| **Entity**                       | **Attributes (PK, FK)**                                      | **Notes**                                     |
| -------------------------------- | ------------------------------------------------------------ | --------------------------------------------- |
| **Member**                       | member_id (PK), Name, Phone_no, Email                        | Member who participates in events or bookings |
| **Event**                        | event_id (PK), Purpose                                       | Events conducted in the library               |
| **Speaker**                      | speaker_id (PK), Name                                        | Guest speakers invited for events             |
| **Booking**                      | booking_id (PK), Booking_date, member_id (FK), event_id (FK) | Member books/registers for an event           |
| **Book**                         | book_id (PK), Title                                          | Represents book used/referenced (inferred)    |
| **Loan / Register / Enrollment** | (No clear PK shown; treated as relationship tables)          | Represent member-event activity               |

### Relationships and Constraints

| **Relationship**                         | **Cardinality**                    | **Participation**                  | **Notes**                                             |
| ---------------------------------------- | ---------------------------------- | ---------------------------------- | ----------------------------------------------------- |
| Member — Booking                         | 1 Member : Many Bookings           | Member (total) → Booking (partial) | One member can book many events                       |
| Event — Booking                          | 1 Event : Many Bookings            | Event (total) → Booking (partial)  | One event can have many member bookings               |
| Event — Speaker                          | 1 Event : 1 Speaker (assumed)      | Event (partial), Speaker (partial) | Event may have a speaker (Has_speaker)                |
| Member — Event (via Enrollment/Register) | Many : Many                        | Both partial                       | Members can enroll/register for multiple events       |
| Book — Event                             | Many Books : Many Events (assumed) | Both partial                       | Events may involve certain books (from Book_id shown) |


### Assumptions
- One member can book or register for many events but each booking is linked to only one event.

- Each event can have one speaker (because “Has_speaker” shows a 1-to-1 style link in the diagram).

- Book_id under event means a book is associated with an event, so events may reference books used or discussed.

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

<img width="632" height="529" alt="image" src="https://github.com/user-attachments/assets/7638412b-f6f1-439f-9576-ce9f21308a20" />

### Entities and Attributes

| **Entity**      | **Attributes (PK, FK)**                                        | **Notes**                                                    |
| --------------- | -------------------------------------------------------------- | ------------------------------------------------------------ |
| **Customer**    | customer_id (PK), Name, Phone                                  | Customer who visits the restaurant                           |
| **Table**       | table_id (PK), Table_num, Capacity                             | Physical dining tables available                             |
| **Waiter**      | waiter_id (PK), Name, Shift                                    | Waiter serving customers                                     |
| **Dish**        | dish_id (PK), Dish_name, Price                                 | Food items ordered by customers                              |
| **Category**    | category_id (PK), Category_name (Starter/Main/Dessert)         | Dish category (belongs_to relationship)                      |
| **Order**       | order_id (PK), customer_id (FK), table_id (FK), waiter_id (FK) | A customer places an order at a table and served by a waiter |
| **Reservation** | reservation_id (PK), customer_id (FK), table_id (FK), Date     | Customer reserves a table                                    |
| **Bill**        | bill_id (PK), order_id (FK), Total_amount                      | Bill generated after the order                               |
| **Dish_Order**  | dish_id (FK), order_id (FK)                                    | Many-to-many link between Dish and Order                     |


### Relationships and Constraints

| **Relationship**              | **Cardinality**                | **Participation**                       | **Notes**                                                        |
| ----------------------------- | ------------------------------ | --------------------------------------- | ---------------------------------------------------------------- |
| Customer — Reservation        | 1 Customer : Many Reservations | Customer (total), Reservation (partial) | A customer can make multiple reservations                        |
| Customer — Order              | 1 Customer : Many Orders       | Customer (total), Order (partial)       | A customer can place multiple orders                             |
| Table — Reservation           | 1 Table : Many Reservations    | Table (total), Reservation (partial)    | Many customers can reserve the same table at different times     |
| Table — Order                 | 1 Table : Many Orders          | Table (total), Order (partial)          | A table can have many orders over time                           |
| Waiter — Order                | 1 Waiter : Many Orders         | Waiter (partial), Order (partial)       | A waiter serves multiple orders                                  |
| Order — Bill                  | 1 Order : 1 Bill               | Both total                              | Each order generates only one bill                               |
| Dish — Category               | Many Dishes : 1 Category       | Dish (partial), Category (total)        | Each dish belongs to one category                                |
| Order — Dish (via Dish_Order) | Many Orders : Many Dishes      | Both partial                            | Orders can contain many dishes; dishes can appear in many orders |


### Assumptions
- One order generates only one bill, and every bill must be linked to an order.

- A dish belongs to exactly one category (Starter, Main, or Dessert).

- A reservation is only for one table at a time, and the same table can be reserved multiple times on different dates.

---

## Result 
  Thus, the ER diagram was created with entities and attributes, Relationships and constraints and assumptions successfully.
