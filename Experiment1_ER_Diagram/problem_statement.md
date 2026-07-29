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

<img width="1021" height="691" alt="image" src="https://github.com/user-attachments/assets/0bdc3f72-083b-47e4-a62c-a97bb1a16358" />


### Entities and Attributes

| Entity                  | Attributes (PK, FK)                                             | Notes                                       |
|-------------------------|-----------------------------------------------------------------|---------------------------------------------|
| Member                  |MemberID (PK), Name, Phone, MembershipType                       |Stores member personal and membership details| 
| Program	                | ProgramID (PK), Type, Duration	                                |Different fitness programs (Yoga, Zumba,etc.)|
| Trainers	              |TrainerID (PK), Name, Phone, Specialization, Experience	        |Trainers working in the gym                  | 
| PersonalTrainingSession	|SessionID (PK), MemberID (FK), TrainerID (FK), Date, Time	      |Personal training session booked by members  | 
| Attendance	            |ID (PK), MemberID (FK), ProgramID (FK), Date, Status	            |Tracks which member attended which program   |
| Payment	                |ID (PK), MemberID (FK), Amount, Date, Mode	                      |Payment records of members                   |

### Relationships and Constraints

| Relationship                   | Cardinality  | Participation       | Notes                              |
|--------------------------------|--------------|---------------------|------------------------------------|
| Member–Program                 |	M:N       	|Partial on both sides|Attendance links Members to Programs|
| Program–Trainers               |	M:N	        |Partial	            |Trainers may run multiple programs  |
| Member–PersonalTrainingSession |	1:M         |Total on PTS side    |Each session must belong to a member|
| Trainer–PersonalTrainingSession|  1:M	        |Total on PTS side	  |Each session requires one trainer   |
| Member–Attendance	             |  1:M	        |Total on Attendance	|Attendance entry refer to a member  | 
| Program–Attendance	           |  1:M	        |Total	              |Attendance linked to programs       |
| Member–Payment	               |  1:M	        |Total on Payment	    |Payment must be made by a member    |

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

<img width="891" height="921" alt="image" src="https://github.com/user-attachments/assets/000c6c71-aa8f-4bf4-8cca-7e968551844f" />


### Entities and Attributes

| Entity     | Attributes (PK, FK)                                                      | Notes                          |
|------------|--------------------------------------------------------------------------|--------------------------------|
|Member      |MemberID (PK), MemberName, Email, Phone	                                  |Library members                 |
|Book	       |BookID (PK), BookName, Author, Genre	                                    |Books available in the library  |
|Loan	       |LoanID (PK), MemberID (FK), BookID (FK), LoanDate, ReturnDate, FineAmount	|Tracks borrowing of books       |
|Room        |RoomID (PK), Capacity, Purpose	                                          |Rooms used for events           |
|Event       |EventID (PK), EventName, EventDate, RoomID (FK)	                          |Events scheduled in the library |
|Speaker     |SpeakerID (PK), Name, Specialization	                                    |Speakers invited for events     |
|EventSpeaker|EventID (FK), SpeakerID (FK)	                                            |Event can have multiple speakers|                   

### Relationships and Constraints

| Relationship | Cardinality | Participation | Notes                                                                  |
|--------------|-------------|---------------|------------------------------------------------------------------------|
|Member–Loan 	 | 1 : M	     |Total on Loan	 |A loan must belong to one member                                        |
|Book–Loan  	 | 1 : M	     |Total on Loan	 |A loan must refer to one book                                           |
|Room–Event	   | 1 : M	     |Total on Event |An event must be assigned a room                                        |    
|Event–Speaker | M : N	     |Partial	       |Eventsmay have multiple speakers,and speakers may attend multiple events|
|Member–Event	 | M : N	     |Partial	       |Members may attend multiple events                                      |
|Book–Member   | M : N	     |Total on both  |Many members can borrow many books over time              |             |


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

<img width="1032" height="692" alt="image" src="https://github.com/user-attachments/assets/1f939055-e752-4135-bf0b-cf18b9bed377" />


### Entities and Attributes

| Entity    | Attributes (PK, FK)                                                                     | Notes                              |
|-----------|-----------------------------------------------------------------------------------------|------------------------------------|
|Customer	  |CustomerID (PK), Name, Email, Contact	                                                  |Customer details                    |      
|Dish	      |DishID (PK), DishName, Price, Category	                                                  |Menu items served                   |
|Waiter	    |WaiterID (PK), Name, Contact, Shift	                                                    |Staff who serve customers           |
|Reservation|ReservationID (PK), CustomerID (FK), TableID, Date, Time  	                              |Table reservations made by customers|
|Orders	    |OrderID (PK), CustomerID (FK), ReservationID (FK), DishID (FK), WaiterID (FK), OrderTime	|Order placed for dishes             | 
|Billing	  |BillID (PK), ReservationID (FK), TotalAmount, ServiceCharge	                            |Final bill for reservation          |               

### Relationships and Constraints

| Relationship        | Cardinality | Participation       | Notes                                      |
|---------------------|-------------|---------------------|--------------------------------------------|
|Customer–Reservation	| 1 : M	      |Total on Reservation	|A reservation must be linked to a customer  |
|Customer–Orders	    | 1 : M	      |Total on Orders	    |An order is always placed by a customer     |
|Reservation–Billing	| 1 : 1	      |Total on Billing	    |Every reservation has exactly one bill      |
|Reservation–Orders	  | 1 : M	      |Partial	            |Not all reservations may have orders        |
|Dish–Orders	        | 1 : M	      |Total on Orders	    |An order must refer to a dish               | 
|Waiter–Orders	      | 1 : M	      |Total	              |Each order is served by one waiter          |
|Customer–Billing	    | 1 : M       |Partial	            |Customer pays the bill for their reservation|         
### Assumptions
- A customer may or may not make a reservation before ordering.
- Each order contains one dish per entry (multiple dishes = multiple order entries).
- Billing is done per reservation, not per individual order.
- A waiter can serve multiple orders but an order is handled by exactly one waiter.

---

## Instructions for Students

1. Complete **all three scenarios** (A, B, C).  
2. Identify entities, relationships, and attributes for each.  
3. Draw ER diagrams using **draw.io / diagrams.net** or hand-drawn & scanned.  
4. Fill in all tables and assumptions for each scenario.  
5. Export the completed Markdown (with diagrams) as **a single PDF**
