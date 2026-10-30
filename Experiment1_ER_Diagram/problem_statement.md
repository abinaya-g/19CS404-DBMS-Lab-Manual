# ER Diagram Workshop – Submission Template

## Objective
To understand and apply ER modeling concepts by creating ER diagrams for real-world applications.

## Purpose
Gain hands-on experience in designing ER diagrams that represent database structure including entities, relationships, attributes, and constraints.

---


##  Scenario C: Restaurant Table Reservation & Ordering

###  Business Context
A popular restaurant wants to manage *reservations, orders, and billing*.

###  Requirements
- Customers can *reserve tables* or walk in.  
- Each reservation includes *date, time, number of guests*.  
- Customers place *food orders linked to reservations*.  
- Each order contains *multiple dishes; dishes belong to **categories* (starter, main, dessert).  
- *Bills* generated per reservation, including food and service charges.  
- *Waiters* assigned to serve reservations.  

###  ER Diagram
<img width="4512" height="2190" alt="erdplus" src="https://github.com/user-attachments/assets/d5af98b1-09fe-4d32-b84a-dca4a6968459" />

###  Entities and Attributes
| Entity    | Attributes (PK, FK) | Notes |
|-----------|----------------------|-------|
| Customer  | CustomerID (PK), Name, Contact | Makes reservations |
| Reservation | ReservationID (PK), Date, Time, Guests, CustomerID (FK), TableID (FK) | Booking info |
| Table     | TableID (PK), Capacity, Location | Dining tables |
| Order     | OrderID (PK), ReservationID (FK), Time | Linked to reservations |
| Dish      | DishID (PK), Name, Category, Price | Ordered item |
| OrderDetail | OrderID (FK), DishID (FK), Quantity | Resolves M:N |
| Bill      | BillID (PK), ReservationID (FK), Amount, ServiceCharge | Final payment |
| Waiter    | WaiterID (PK), Name | Assigned to reservations |

###  Relationships and Constraints
| Relationship | Cardinality | Participation | Notes |
|--------------|-------------|---------------|-------|
| Customer–Reservation | 1:N | Partial | A customer can have multiple reservations |
| Reservation–Table | 1:1 | Total | One reservation per table |
| Reservation–Order | 1:N | Total | Orders linked to reservation |
| Order–Dish | M:N | Total | Resolved using OrderDetail |
| Reservation–Bill | 1:1 | Total | One bill per reservation |
| Reservation–Waiter | 1:1 | Partial | Assigned waiter |

###  Assumptions
- Each reservation *occupies one table* only.  
- Bills always generated *per reservation*.  
- Service charges fixed percentage (not modeled).  

---
##  Instructions for Students
1. Complete *all three scenarios (A, B, C)*.  
2. Identify *entities, relationships, and attributes* for each scenario.  
3. Draw ER diagrams using *draw.io / diagrams.net* (or hand-drawn & scanned).  
4. Fill in *Entities, Relationships, Assumptions* tables.  
5. Export the completed Markdown (with diagrams) as a *single PDF*.  

---

  End of Submission Template
