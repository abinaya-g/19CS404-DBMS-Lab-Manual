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
<img width="686" height="503" alt="image" src="https://github.com/user-attachments/assets/a9776459-79ff-4c6f-a8ec-89a83329beda" />


### Entities and Attributes

<img width="732" height="522" alt="image" src="https://github.com/user-attachments/assets/744b06f0-8a00-42c3-bf23-1303b22742a4" />


### Relationships and Constraints


<img width="667" height="472" alt="image" src="https://github.com/user-attachments/assets/4a12c98b-79c7-4288-afba-6dd101b9e9e5" />


### Assumptions

Each member has a unique member_id. 

Programs are predefined (Yoga, Zumba, Weight Training).   

A member can join the same program only once at a time.

Each personal training session is handled by only one trainer. 

Attendance is mandatory for every booked personal training session. 

Payments include both membership fees and personal training session fees.

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
<img width="702" height="852" alt="image" src="https://github.com/user-attachments/assets/467b92c3-820c-4c15-90b6-45c2c4b34e6e" />


### Entities and Attributes

<img width="666" height="600" alt="image" src="https://github.com/user-attachments/assets/9594b18b-e57d-4b2b-b9ab-33742b3b7202" />


### Relationships and Constraints

<img width="522" height="755" alt="image" src="https://github.com/user-attachments/assets/04f26a52-0575-481a-b6d3-5cdff7f9f00c" />


### Assumptions

Each member is uniquely registered.

A member can borrow many books; each loan is for one book. 

A book can be loaned many times, but only once at a time. 

Loan stores start and return dates. 

Fine is generated only for late returns (one fine per loan).

Events can have many speakers and many members. 

Each event is booked in one room; rooms can host many events. 

Members can attend multiple events. 

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

<img width="732" height="821" alt="image" src="https://github.com/user-attachments/assets/b030134e-4c36-429a-a1f9-d979be114e84" />


### Entities and Attributes

<img width="720" height="676" alt="image" src="https://github.com/user-attachments/assets/03a7e2f2-536c-4257-942a-13eb3324574c" />

### Relationships and Constraints

<img width="720" height="722" alt="image" src="https://github.com/user-attachments/assets/e6a46487-887a-4123-b044-fcc554a2d1e4" />
 

### Assumptions

Each Customer is uniquely identified by Customer_ID. 

A customer can place multiple orders, but each order belongs to one customer.

A customer can make multiple reservations. 

Each Reservation is for one table at a specific date and time. 

A Table can be reserved many times, but only once at a given time. 

Each reservation is served by one waiter. 

A waiter can serve multiple reservations. 

Each reservation generates one bill. 

Each bill belongs to one reservation. 

## Instructions for Students

1. Complete **all three scenarios** (A, B, C).  
2. Identify entities, relationships, and attributes for each.  
3. Draw ER diagrams using **draw.io / diagrams.net** or hand-drawn & scanned.  
4. Fill in all tables and assumptions for each scenario.  
5. Export the completed Markdown (with diagrams) as **a single PDF**
