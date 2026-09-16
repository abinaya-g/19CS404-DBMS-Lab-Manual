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

# ER Diagram Submission - Student Name

## Scenario Chosen:
University 

## ER Diagram:

![er diagram university](https://github.com/user-attachments/assets/571fb603-3cac-4921-a335-f04756f16b2c)


## Entities and Attributes:
- University -
  Reg. No,Address,Student,DOB
- Mail ID -
  Course,Mobile No,Faculty
- Course -
  Course Code,Credits,Prerequisite,Students Enrolled,Course Name
- Instructors -
  Name,Course Taken,Address,Experience


## Relationships and Constraints:
- University–Student Relationship
Cardinality: One-to-Many (A university can have many students, but each student belongs to one university.)
Participation: Total (Every student must be associated with a university.)

- Student–Course Relationship
Cardinality: Many-to-Many (A student can enroll in multiple courses, and a course can have multiple students.)
Participation: Partial (A student may or may not enroll in a course.)

- Course–Instructor Relationship
Cardinality: Many-to-Many (A course can be taught by multiple instructors, and an instructor can teach multiple courses.)
Participation: Partial (A course may exist without an instructor assigned initially.)

- Extension (Prerequisite):
  In the course entity, prerequisites are modeled as an attribute indicating which course(s) must be completed before enrolling in the course. This adds dependency between different course entities.

## Design Choices:
- Entities:
Entities were chosen based on major participants in a university system (University, Student, Course, Instructor).
- Relationships:
Relationships were modeled to reflect real-world connections: students belong to a university, enroll in courses, and courses are conducted by instructors.
- Attributes:
Attributes cover important details needed for university operations — e.g., student contacts, course details, instructor background.
- Assumptions:
Each student belongs to only one university.
Courses can have prerequisites, but it’s optional.
Instructors can take multiple courses and have their own experiences noted separately.
Some relationships are partial, meaning entities can exist without always needing the related entity immediately (e.g., a course can exist before any students enroll).

## RESULT
Thus the ER daigram have been successfully drawn and explained briefly.
