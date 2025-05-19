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
University / Hospital (choose one)

## ER Diagram:

![Screenshot 2025-04-29 192421](https://github.com/user-attachments/assets/04438c41-e3e7-443d-ab3a-3c34ad3cbb3e)


## Entities and Attributes:
1. Student

   Attributes:

   Student ID

   Name

   Address

   Telephone

   Date of Birth

   NID

2. Enrollment

   Attributes:

   Enrollment Date

   Course Name

3. Lecturer

   Attributes:

   Lecturer ID

   Name

   Address

   Telephone

   Email

4. Subjects

   Attributes:

   Subject Code

   Subject Unit

   Subject Desc

5. Lecture

   Attributes:

   CC ID

   Subject

   Date

   Time

   Lecturer Name

## Relationships and Constraints:
 1. enrolls (between Enrollment and Student)

    Cardinality:

    One Enrollment → many Students (1:N)

    Participation:

    Total participation of Enrollment (each enrollment must be associated with a student)

    Partial participation of Student (not every student must be enrolled)

2. lectures (between Lecturer and Lecture)

   Cardinality:

   One Lecturer → many Lectures (1:N)

   Participation:

   Total participation of Lecture (every lecture must have a lecturer)

   Partial participation of Lecturer (a lecturer might not give any lectures)

3. Lecture–Subjects relationship

   Cardinality:

   Many Lectures → one Subject (N:1)

   Participation:

   Total participation of Lecture (each lecture is about one subject)

   Partial participation of Subject (not every subject must have a lecture)
   
## Extension (Prerequisite / Billing):

-Prerequisite is a recursive relationship on the Subjects entity.
It represents that one subject may require completion of another subject before it.
Cardinality is many-to-many (M:N) with partial participation from both sides.

## Design Choices:

1. Many-to-Many Relationship: Since each student can take many subjects and each subject can be taken by many students, a many-to-many relationship is appropriate.

2. Associative Entity: Model Result as an associative entity with attributes like grade, marks, or status to store performance details.

3. Total Participation from Result: Every Result must be linked to both a Student and a Subject, ensuring referential integrity.


## RESULT

Result is a relationship between Student and Subjects.
It captures the performance of a student in a subject (e.g., marks, grade).
Cardinality is many-to-many (M:N), with attributes like grade or score.
