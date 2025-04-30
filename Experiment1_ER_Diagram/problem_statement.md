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

# ER DIAGRAM SUBMISSION :
---
STUDENT NAME : DIVYASHREE G

REGISTER NUMBER : 212223060062

## SCENARIO CHOSEN :
 Hospital ER Diagram

## ER DIAGRAM :

![image](https://github.com/user-attachments/assets/b4c490a8-4dd3-42fd-b0ee-710dc0916f85)

## ENTITIES & ATTRIBUTES :

PATIENT - PATIENT ID, NAME, DOB, GENDER <br>
DOCTOR - DOCTOR ID, NAME, SPECIALIZATION, PHONE NUMBER <br>
DEPARTMENT - DEPT ID, NAME, DEPARTMENT HEAD <br>
MEDICAL RECORD - MEDICAL RECORD ID, PATIENT MED. DETAILS, MEDICAL PRESCRIBED <br>
APPOINTMENT - APPOINTMENT ID, REASON FOR VISIT, APPOINTMENT DATE & TIME <br>
PAYMENT - BILL NUMBER, PAYMENT DATE, PAYMENT MODE
...

## RELATIONSHIPS & CONSTRAINTS :
---

Consults (Patient → Doctor)  <br>
Cardinality: Many-to-Many <br>
Participation: Partial <br>


Manages (Doctor → Department) <br>
Cardinality: Many-to-Many <br> 
Participation: Partial  <br>


Handles (Department → Payment) <br>
Cardinality: One-to-Many (One department can handle many payments)  <br>
Participation: Partial  <br>


Personal Data Is (Patient → Medical Record) <br>
Cardinality: One-to-Many  <br>
Participation: Total (Every medical record is linked to one patient)  <br>


Derived From (Medical Record → Appointment) <br>
Cardinality: Many-to-Many  <br>
Participation: Partial  


Cost of Consultation (Appointment → Payment) <br>
Cardinality: Many-to-Many <br> 
Participation: Partial  <br>

---
## EXTENSIONS (Pre-requisite/billing) :

The billing process in the ER model is represented through the PAYMENT entity, which captures all necessary details related to a patient's financial transactions. This entity includes attributes such as Bill Number, Payment Date, and Payment Mode to store information about individual payment instances. The Cost of Consultation relationship between APPOINTMENT and PAYMENT is modeled as a many-to-many relationship, allowing flexibility for scenarios where a single appointment can involve multiple payments (e.g., part payments) or one payment can cover multiple appointments (e.g., bundled services). Additionally, the Handles relationship connects the DEPARTMENT entity to PAYMENT in a one-to-many manner, indicating that a department can manage multiple payments, although a specific payment is handled by only one department. This structure enables the system to efficiently track billing operations, identify responsible departments, and maintain a record of all transactions associated with appointments.

## DESIGN CHOICES :

Key entities like Patient, Doctor, Appointment, Department, Medical Record, and Payment were chosen to cover all essential hospital operations. Relationships such as Consults, Assign, and Cost of Consultation reflect real-world interactions like doctor visits and billing. Many-to-many and total participation were used where needed for accuracy, such as every medical record being linked to a patient. We assumed that departments handle payments to reflect administrative structure. Overall, the design ensures clarity, real-world relevance, and future scalability.

## RESULT :

Thus, the ER diagram for the hospital management system was successfully designed, with appropriate entities, relationships, and constraints that accurately model the real-world healthcare environment.
