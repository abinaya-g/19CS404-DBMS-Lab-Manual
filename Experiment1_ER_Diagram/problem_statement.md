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

### Hospital

## ER Diagram:

![Workshop_Hospital](https://github.com/user-attachments/assets/546f1822-55e9-42e6-9751-f3395d4863a4)

## Entities and Attributes:
Hospital:
Attributes: Hospital_ID (Primary Key), Name, Contact_Details

Doctors:
Attributes: Doctor_ID (Primary Key), Name, Hospital_ID (Foreign Key)

Patients:
Attributes: ID (Primary Key), Name, Desc, Doctor_ID (Foreign Key)

Appointment:
Attributes: Appointment_ID (Primary Key), Date, Patient_ID (Foreign Key)

Medical Record:
Attributes: Report_No (Primary Key), Appointment_ID (Foreign Key), Dept
...

## Relationships and Constraints:
Contains (Hospital ↔ Doctors)

Cardinality: 1 Hospital : N Doctors

Participation: Total on Hospital (mandatory 1) and Partial on Doctors (a Doctor must belong to a Hospital)

Treats (Doctors ↔ Patients)

Cardinality: N Doctors : N Patients

Participation: Partial for both (a Doctor may or may not treat many Patients; a Patient may be treated by multiple Doctors)

Books (Patients ↔ Appointment)

Cardinality: 1 Patient : N Appointments

Participation: Total on Appointment (every Appointment must be booked by a Patient)

Receives (Patients ↔ Medical Record)

Cardinality: N Patients : N Medical Records

Participation: Partial for both (a Patient may have multiple Medical Records, a Record must belong to a Patient)
...

## Extension (Prerequisite / Billing):
- Explain how you modeled prerequisites or billing.

## Design Choices:
Entities:
Chose Hospital, Doctors, Patients, Appointment, and Medical Record to represent key parts of a healthcare system.

Relationships:

Hospital Contains Doctors (1:N) – A hospital has many doctors.

Doctor Treats Patient (N:N) – Doctors can treat many patients, and patients can have many doctors.

Patient Books Appointment (1:N) – A patient can book multiple appointments.

Patient Receives Medical Record (N:N) – Patients receive multiple medical records linked to appointments.

Assumptions:

Each doctor works in one hospital.

Each appointment is booked by one patient.

Medical records are created only after an appointment.

## RESULT
