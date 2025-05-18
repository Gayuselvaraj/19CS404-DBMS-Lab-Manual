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
![DBMS](https://github.com/user-attachments/assets/94fe52db-0b01-42d4-bcc6-e5370c1bcc4d)



## Entities and Attributes:
```
Patient - Patient_ID (PK), Name, Gender, Date of Birth (DoB), Address, Phone No., Email, Insurance

Doctor - ID (PK), Name, Specialization, Phone No., Email, Work Schedule

Appointment - Appointment_ID (PK), Date, Time

Medical Records - ID (PK), Diagnosis

Billing - Billing_ID (PK), Patient_ID (FK), Amount, Billing Date, Payment Status

Department - Dept_ID (PK), Dept_Name, Dept_Head, Room No.
```

## Relationships and Constraints:
Book (Patient → Appointment)

Cardinality: Many-to-Many Participation: Total (Every appointment must involve at least one patient)

Assign (Appointment → Doctor)

Cardinality: Many-to-One Participation: Total (Each appointment must be assigned to a doctor)

Associate (Patient → Medical Records)

Cardinality: One-to-Many Participation: Partial (A patient may or may not have medical records)

Maintain (Doctor → Medical Records)

Cardinality: One-to-Many Participation: Partial (Doctors maintain multiple records)

Receive (Patient → Billing)

Cardinality: One-to-Many Participation: Partial (Patients may have multiple billing records)

Specialization (Doctor → Department)

Cardinality: Many-to-One Participation: Partial (Doctor specializes in a department)

## Extension (Prerequisite / Billing):
Billing was modeled by connecting Patient to Billing through the "Receive" relationship, where billing entries are generated for each patient based on services received. The Billing entity includes attributes like Billing_ID, Amount, Billing Date, and Payment Status to track financial transactions independently but linked via Patient_ID.

## Design Choices:

Entities like Patient, Doctor, and Appointment are core in any healthcare system, so they were naturally included. Medical Records are associated separately for flexibility — allowing multiple diagnoses per patient and doctor. Billing is separated to maintain financial records cleanly, keeping healthcare service records independent from financial operations. Departments were created for Doctors to properly map organizational hierarchy and specialization. Many-to-Many relationships like Book and Assign are handled with associative entities (like Appointment) to simplify complex scheduling scenarios.

## RESULT
Thus, the ER diagram for the hospital management system was successfully designed, and the entities, relationships, and constraints were clearly represented.
