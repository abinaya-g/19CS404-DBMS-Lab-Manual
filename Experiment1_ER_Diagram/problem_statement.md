# Experiment 1: Entity-Relationship (ER) Diagram

## 🎯 Objective:
To understand and apply the concepts of ER modeling by creating an ER diagram for a real-world application.

## 📚 Purpose:
The purpose of this workshop is to gain hands-on experience in designing ER diagrams that visually represent the structure of a database including entities, relationships, attributes, and constraints.

### 🔹 Scenario: University Database
Design a database to manage students, instructors, programs, courses, and student enrollments. Include prerequisites for courses.

**User Requirements:**
- Academic programs grouped under departments.
- Students have admission number, name, DOB, contact info.
- Instructors with staff number, contact info, etc.
- Courses have number, name, credits.
- Track course enrollments by students and enrollment date.
- Add support for prerequisites (some courses require others).

## 📝 Tasks:
1. Identify entities, relationships, and attributes.
2. Draw the ER diagram using any tool (draw.io, dbdiagram.io, hand-drawn and scanned).
3. Include:
   - Cardinality & participation constraints
   - Prerequisites for University OR Billing for Hospital
4. Explain:
   - Why you chose the entities and relationships.
   - How you modeled prerequisites or billing.

# ER Diagram Submission:
Dharshni V M - 212223240029

## Scenario Chosen:
University 

## ER Diagram:
![ER 1 drawio](https://github.com/user-attachments/assets/a7eb4a36-f4e4-48eb-b868-acced1ef457d)

## Entities and Attributes:
```
Student - ID, Name, DOB, Email, Contact
Instructor - ID, Name, Age, Email, Contact
Department - Dep ID, Dep Name, Dep Head, Dep Code
Course - Code, Name, Category, Credit, Prerequisites
```

## Relationships and Constraints:
```
Relationships and Constraints

1. Student belongs to Department
   - Cardinality: Many-to-One (N:1)
   - Participation: Total participation from Student side

2. Student enrolls in Course
   - Cardinality: Many-to-Many (M:N)
   - Participation: Partial participation from Student side

3. Student mentored by Instructor
   - Cardinality: Many-to-One (N:1)
   - Participation: Partial participation from Student side

4. Instructor teaches Course
   - Cardinality: Many-to-Many (M:N)
   - Participation: Partial participation from Instructor side

5. Department has Course
   - Cardinality: One-to-Many (1:N)
   - Participation: Total participation from Course side
```

## Extension (Prerequisite):
In the ER diagram, prerequisites are modeled as a recursive relationship within the COURSE entity, where one course can be a prerequisite for many others. The relationship is one-to-many (1:N) with partial participation, since not all courses require a prerequisite. This is represented through a "Prerequisites" attribute that references another course's ID within the same entity.

## Design Choices:
College: Chose College as the top-level unit managing multiple departments.

Department: Handles both students and courses, organizing academic structure.

Student: Tracks enrollments and is associated with a department.

Course: Represents subjects offered by departments.

Faculty: Represents who teaches the courses.

Relationships:

Offers: College offers departments.

Has Student: Department has students.

Includes: Department includes courses.

Is Taught By: Courses are taught by faculty.

Prerequisites: Modeled as a self-referencing link within the Course entity.

Assumptions: Departments belong to colleges, courses belong to departments, not all departments have students, and not all courses have prerequisites.

## RESULT:
Thus, this project effectively models a university database system through an ER diagram, clearly representing the relationships among colleges, departments, students, instructors, courses, and enrollments, with support for course prerequisites.
