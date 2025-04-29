# Experiment 1: Entity-Relationship (ER) Diagram

## 🎯 Objective:
To understand and apply the concepts of ER modeling by creating an ER diagram for a real-world application.

## 📚 Purpose:
The purpose of this workshop is to gain hands-on experience in designing ER diagrams that visually represent the structure of a database including entities, relationships, attributes, and constraints.

---

## 🧪 Choose One Scenario:

### 🔹 Scenario 1: University Database
Design a database to manage students, instructors, programs, courses, and student enrollments. Include prerequisites for courses.

**User Requirements:**
- Academic programs grouped under departments.
- Students have admission number, name, DOB, contact info.
- Instructors with staff number, contact info, etc.
- Courses have number, name, credits.
- Track course enrollments by students and enrollment date.
- Add support for prerequisites (some courses require others).

---

### 🔹 Scenario 2: Hospital Database
Design a database for patient management, appointments, medical records, and billing.

**User Requirements:**
- Patient details including contact and insurance.
- Doctors and their departments, contact info, specialization.
- Appointments with reason, time, patient-doctor link.
- Medical records with treatments, diagnosis, test results.
- Billing and payment details for each appointment.

---

## 📝 Tasks:
1. Identify entities, relationships, and attributes.
2. Draw the ER diagram using any tool (draw.io, dbdiagram.io, hand-drawn and scanned).
3. Include:
   - Cardinality & participation constraints
   - Prerequisites for University OR Billing for Hospital
4. Explain:
   - Why you chose the entities and relationships.
   - How you modeled prerequisites or billing.

# ER DIAGRAM SUBMISSION  
## STUDENT NAME : DIVYASHREE G
## REGISTER NUMBER : 212223060062

## SCENARIO CHOSEN:
University ER Diagram

## ER DIAGRAM :

![DIVYASHREE G 212223060062 DBMS-21 drawio (1)](https://github.com/user-attachments/assets/226c089d-facd-4ce4-8cc4-b46a0a5b2d34)


## ENTITIES AND ATTRIBUTES :

STUDENT - Name,Register Number, Email ID, Phone Number, DOB, Subjects Enrolled

DEPARTMENT - Department Name, DepartmentID

PROGRAM - Program Name , Program Code , Subjects

COURSE - Course Name , Course Code ,  Credits

FACULTIES - Name, Faculty ID ,Subject

UNIVERSITY - University Name, ID, Students & Faculties


## RELATIONSHIP AND CONSTRAINTS :
---

### **IsIn (Student → Department)**  
Cardinality: Many-to-One <br>  
Participation: Total (Each student must belong to one department)

---
### **Provides (Department → Program)**  
Cardinality: Many-to-Many <br>  
Participation: Partial (A department may or may not offer multiple programs)

---
### **Contains (Program → Course)**  
Cardinality: One-to-Many 

Participation: Partial (A program may or may not contain courses)

---
### **Handles (Faculties → Course)**  
Cardinality: Many-to-Many <br>  
Participation: Partial (A faculty may or may not handle courses)

---
### **Has (University → Faculties)**  
Cardinality: One-to-Many <br>  
Participation: Total (Each university has faculties)
---
### Relationship (University → Student)  
Cardinality: One-to-Many <br>  
Participation: Total (Each university has students)

## EXTENSION :
To model prerequisites, we can add a recursive relationship on the Course entity called "Prerequisite", where one course can be a prerequisite for another. This would be a one-to-many relationship (one course can be a prerequisite for many other courses), and participation would typically be partial, as not all courses have prerequisites.

For billing, a new entity called "Billing" can be introduced, linked to the Student entity through a "Pays" relationship. The Billing entity would include attributes such as billing ID, amount, due date, and payment status. This relationship would be one-to-many, where one student can have multiple billing records, and participation from the student side could be total, assuming all students must pay fees.

These extensions maintain normalization while supporting additional academic and financial requirements.

## DESIGN CHOICES:
The ER model includes key entities like Student, Department, Program, Course, Faculties, and University, each with relevant attributes to represent an academic system. Relationships such as IsIn, Provides, Contains, Handles, and Has reflect real-world connections between students, departments, programs, and faculty. Total participation is used where association is mandatory (e.g., students must belong to a department), and partial where optional. Many-to-many relationships allow flexibility, especially in course and faculty handling. These design choices ensure clarity, data consistency, and scalability

## RESULT :
Thus,the ER Diagram for University is successfully designed and entities,relationships and constraints were clearly represented.
