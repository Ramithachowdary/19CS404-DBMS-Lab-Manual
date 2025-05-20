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

# ER Diagram Submission - Ramitha chowdary S - 212224240130

## Scenario Chosen:
Hospital 

## ER Diagram:
![image](https://github.com/user-attachments/assets/321daa76-335d-407a-826b-15493c10b918)


## Entities and Attributes:
```
College-ID,Name
Department-Dept ID,Dept Name
Student-Student Id, Enrollment Id, Course Id, Enrollment Date
Course-Course Id, Course Name
Faculty-Teachers Id, Teachers name, Phone/email
```

## Relationships and Constraints:
```
College offers Department
Cardinality: One-to-Many (1:N)
Participation: Total participation from Department side

Department has Student
Cardinality: One-to-Many (1:N)
Participation: Partial participation from Department side

Department includes Course
Cardinality: One-to-Many (1:N)
Participation: Total participation from Course side

Course is taught by Faculty
Cardinality: Many-to-Many (M:N)
Participation: Partial participation from Course side

Course has Prerequisite (Course → Course)
Cardinality: One-to-Many (1:N)
Participation: Partial participation from Course side
```

## Extension (Prerequisite / Billing):
Prerequisites are modeled as a recursive relationship on the Course entity, meaning one course can require another course before enrollment. Cardinality is 1:N (one course can have many prerequisites) and participation is partial (not all courses must have prerequisites).

## Design Choices:
I chose College as the top-level unit managing multiple departments. Departments were needed to handle both students and courses. Students are important to track enrollments, while Courses represent the subjects offered. Faculty was added to show who teaches these courses. Relationships like offers, has student, includes, and in taught connect everything just like in real life. The prerequisite is a special self-link showing that some courses depend on others. I assumed every department belongs to a college, courses belong to departments, but not all departments must have students or all courses have prerequisites. This keeps the design simple, practical, and close to how colleges actually work.
## RESULT
The ER Diagram for Universitywas successfully created.Identifying the keyentities, attributes, and the relationships
