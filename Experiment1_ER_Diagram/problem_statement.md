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
![Workshop (2)](https://github.com/user-attachments/assets/e974c5a8-c689-487c-929a-882872d7605d)

## Entities and Attributes

### University:
- **University_ID** (Primary Key)
- **Name**
- **Contact_Details**

### Departments:
- **ID** (Primary Key)
- **Name**
- **Description**

### Faculty:
- **Lecturer_ID** (Primary Key)
- **Name**
- **University_ID** (Foreign Key)

### Course:
- **Course_ID** (Primary Key)
- **Course_Name**
- **Description**
- **Lecturer_ID** (Foreign Key)

### Student:
- **ID** (Primary Key)
- **Name**
- **Department**

### Enrollment (Associative Entity):
- **Student_ID** (Foreign Key)
- **Course_ID** (Foreign Key)

---

## Relationships and Constraints

### Contains (University → Faculty):
- **Cardinality**: 1 (University) : N (Faculty)
- **Participation**: Total from Faculty side (each faculty must belong to a university)

### Teaches (Faculty → Course):
- **Cardinality**: N (Faculty) : N (Course)
- **Participation**: Partial (a faculty can teach multiple courses or none)

### Offers (Departments → Course):
- **Cardinality**: 1 (Department) : N (Course)
- **Participation**: Total from Course side (each course must belong to a department)

### Has Prerequisite (Course → Course):
- **Cardinality**: M (Course) : N (Prerequisite Course)
- **Participation**: Optional (some courses may not have prerequisites)

### Enrollment (Student → Course):
- **Cardinality**: M (Student) : N (Course)
- **Participation**: Partial (students may enroll in multiple or no courses)

### Completed Prerequisite (Student → Course):
- **Cardinality**: M (Student) : N (Prerequisite Course)
- **Participation**: Optional (students may or may not have completed all prerequisites)

---

## Extension (Prerequisite / Billing)

### Prerequisite Modeling:
- **"Has Prerequisite"** is modeled as a recursive relationship within the Course entity itself.
- **"Completed Prerequisite"** is modeled as a separate relationship connecting Student to Course directly, indicating which prerequisite courses have been completed by each student.


## Design Choices

### Separate Enrollment Entity:
- Chosen to handle the M:N relationship between Students and Courses, allowing future attributes like **"enrollment date"**, **"grade"**, etc.

### Recursive Relationship for Prerequisites:
- Courses often depend on other courses; modeling **"Has Prerequisite"** within the Course entity allows this relationship to be naturally represented.

### University-Faculty Structure:
- Made University responsible for Faculty to properly represent institutional hierarchies and maintain a clear structure between universities and their faculty members.

### Departments and Courses:
- Courses belong to a Department, which allows for organized classification across academic units, helping to streamline course management within each department.

### Flexibility and Scalability:
- The design is kept flexible for easy future additions like **Billing**, **Grades**, **Academic Year**, and other features, enabling future expansion without significant restructuring.


## RESULT
Thus the ER Diagram for an University Management is created successfully
