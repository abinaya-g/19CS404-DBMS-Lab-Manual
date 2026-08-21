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
*Paste or attach your diagram here*  
<img width="1021" height="691" alt="image" src="https://github.com/user-attachments/assets/140bc193-f446-4c70-b937-c280503efd46" />

### Entities and Attributes

<img width="1281" height="350" alt="image" src="https://github.com/user-attachments/assets/a50f04c0-88cf-4359-98c9-acd43cd4c803" />


### Relationships and Constraints

<img width="1065" height="373" alt="image" src="https://github.com/user-attachments/assets/50b43f72-4b16-4b6b-a6d8-deaa9c4dcb6c" />


### Assumptions

- A member can join multiple programs.
- Trainers can be assigned to multiple programs.
- Personal training sessions always involve one trainer and one member.

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
*Paste or attach your diagram here*  
<img width="891" height="921" alt="image" src="https://github.com/user-attachments/assets/f8693b6e-20a6-4f2c-8528-35bb2380607a" />

### Entities and Attributes

<img width="1201" height="380" alt="image" src="https://github.com/user-attachments/assets/a31d445e-08a5-47d1-922f-35a4fff1ef3d" />


### Relationships and Constraints

<img width="1162" height="332" alt="image" src="https://github.com/user-attachments/assets/3ba5fe19-201c-475a-a48f-26b3ae2b9a32" />


### Assumptions

- A member can borrow multiple books, but each loan entry is for one book at a time.
- FineAmount is calculated separately and stored in the Loan entity.
- A room can host many events but an event can take place in only one room.

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
*Paste or attach your diagram here*  
<img width="1032" height="692" alt="image" src="https://github.com/user-attachments/assets/de3f9ad3-79ed-40c9-991f-707ef78d4f34" />

### Entities and Attributes

<img width="1282" height="392" alt="image" src="https://github.com/user-attachments/assets/96917901-53ec-4296-a546-11e0034a89bb" />


### Relationships and Constraints

<img width="1007" height="390" alt="image" src="https://github.com/user-attachments/assets/34d993ea-a888-40f8-b5b5-8b70cbcf8cdc" />

### Assumptions

- A customer may or may not make a reservation before ordering.
- Each order contains one dish per entry (multiple dishes = multiple order entries).
- Billing is done per reservation, not per individual order.

---

## Instructions for Students

1. Complete **all three scenarios** (A, B, C).  
2. Identify entities, relationships, and attributes for each.  
3. Draw ER diagrams using **draw.io / diagrams.net** or hand-drawn & scanned.  
4. Fill in all tables and assumptions for each scenario.  
5. Export the completed Markdown (with diagrams) as **a single PDF**
