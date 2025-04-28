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

![Screenshot 2025-04-28 135902](https://github.com/user-attachments/assets/8d70faae-a8c7-4102-8039-3b80951253bc)

## Entities and Attributes:
- Department: Dept ID,Dept Name
- Student: Reg No,Name,Date of Birth,Email,Phone No,Dept Name,Program Name
- Course:Course ID,Course Name,Program Name,Credits,Lab/Theory
- Professor:Teacher ID,Name,Phone No,Course ID
- Prerequisite:Prerequisite Course ID,Prerequisite Course Name,Course Name

...

## Relationships and Constraints:
- Admission (Many-to-One, Student-Department)
- Enrollment (Many-to-Many, Student-Course)
- Taught by (One-to-Many,Professor-Course)
- Before Enrollment (One-to-Many,Course-Prerequisite)
...

## Extension (Prerequisite):

- Each Course can have zero or more prerequisites.
- A Prerequisite Course itself must exist in the Course entity.
- The Prerequisite entity acts almost like a self-referencing relationship:
- Both course_id and prerequisite_course_id come from the same Course table.
- The relation Before Enrollment enforces that the prerequisite must be satisfied before a student enrolls in the course.
- Both course_id and prerequisite_course_id are foreign keys referencing the Course table.
- Together they form a composite primary key to ensure uniqueness (no duplicate prerequisites).

## Design Choices:

### Entities

- Department : Chosen because departments organize students and courses into academic units.
- Student : Central entity; students need to be tracked individually for admissions, enrollments, and personal information.
- Course : Necessary to represent the subjects or classes students enroll in.
- Professor : Needed to manage which faculty teaches which course. 
- Prerequisite : Modeled as a separate entity to manage the complex dependency between courses.

### Relationships

- Admission (Student - Department):Captures the student's assignment to an academic department at the time of admission.
- Enrollment (Student - Course):Models the many-to-many relationship because students can take multiple courses and courses have many students.
- Taught by (Professor - Course):Needed because a professor can teach multiple courses.
- Before Enrollment (Course - Prerequisite):Allows tracking of course dependencies, ensuring proper academic progression.

## RESULT

The Given ER Diagram is done and the output is verified.
