# ER Diagram Workshop 

## Objective
To understand and apply ER modeling concepts by creating ER diagrams for real-world applications.

## Purpose
Gain hands-on experience in designing ER diagrams that represent database structure including entities, relationships, attributes, and constraints.

---

# Scenario A: City Fitness Club Management

Scenario A: City Fitness Club Management

Business Context:
FlexiFit Gym wants a database to manage its members, trainers, and fitness programs.

## Requirements:

Members register with name, membership type, and start date.

Each member can join multiple programs (Yoga, Zumba, Weight Training).

Trainers assigned to programs; a program may have multiple trainers.

Members may book personal training sessions with trainers.

Attendance recorded for each session.

Payments tracked for memberships and sessions.

## ER Diagram:

<img width="1536" height="1024" alt="image" src="https://github.com/user-attachments/assets/83e13b61-0662-4dfd-b75d-0dd069cfdc48" />

Create a diagram in draw.io using the following entities and relationships.

## Entities and Attributes
Entity	Attributes (PK, FK)	Notes
Member	MemberID (PK), Name, MembershipType, StartDate	Stores member info
Trainer	TrainerID (PK), Name, Expertise	Trainer info
Program	ProgramID (PK), ProgramName, Duration	Fitness programs
Session	SessionID (PK), MemberID (FK), TrainerID (FK), Date, Time	Personal training sessions
Payment	PaymentID (PK), MemberID (FK), Amount, Date, PaymentType	Membership and session payments
Relationships and Constraints
Relationship	Cardinality	Participation	Notes
Member-Program	Many-to-Many	Optional	Members can join multiple programs; programs have multiple members
Trainer-Program	Many-to-Many	Optional	Trainers can handle multiple programs
Member-Session	One-to-Many	Mandatory	A member may have multiple personal sessions
Trainer-Session	One-to-Many	Mandatory	A trainer may handle multiple sessions
Member-Payment	One-to-Many	Mandatory	Payments recorded per member
## Assumptions

Each session has only one trainer and one member.

Membership types are predefined (Monthly, Quarterly, Annual).

Attendance is tracked within Session entity.

---


