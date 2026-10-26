
# Assignment III: SQL Table Manipulation
* **Student Name:** Niyongabo Blaise Pascal
* **Student ID:** 202513244 
* **Institution:** Kigali Independent University (ULK)[span_3](start_span)[span_3](end_span)
* **Instructor:** Eric Maniraguha[span_4](start_span)[span_4](end_span)
* **Chosen Business Idea:** Student Registration System[span_5](start_span)[span_5](end_span)[span_6](start_span)[span_6](end_span)
* **Selected DBMS:** PostgreSQL / MySQL 8.0[span_7](start_span)[span_7](end_span)

---

## 1. Project Overview
This project involves designing, creating, and managing a relational database for a Student Registration System[span_8](start_span)[span_8](end_span)[span_9](start_span)[span_9](end_span). It demonstrates table creation, primary and foreign key constraints, data insertion, data retrieval (`SELECT` and `JOIN`), data modification (`UPDATE`), table structure alterations (`ALTER TABLE`), and constraint verification[span_10](start_span)[span_10](end_span)[span_11](start_span)[span_11](end_span)[span_12](start_span)[span_12](end_span)[span_13](start_span)[span_13](end_span).

---

## 2. Database and Table Design
* **Database Name:** `niyongaboblaise_20241234_student_registration_system`[span_14](start_span)[span_14](end_span)
* **Tables:**
  1. `departments`: Stores academic department details (Parent table).
  2. `students`: Stores individual student details and links to departments (Child table).
  3. `enrollments`: Manages course registrations for students and links to students (Child table).

### **Entity-Relationship Diagram (ERD)**
![ERD](erd.png)

---

## 3. SQL Statements & Practical Tasks

### **3.1 Database and Table Creation**
```sql
CREATE DATABASE niyongaboblaise_20241234_student_registration_system;

CREATE TABLE departments (
    department_id SERIAL PRIMARY KEY,
    department_name VARCHAR(100) NOT NULL,
    office_location VARCHAR(50)
);

CREATE TABLE students (
    student_id SERIAL PRIMARY KEY,
    first_name VARCHAR(50) NOT NULL,
    last_name VARCHAR(50) NOT NULL,
    email VARCHAR(100) UNIQUE NOT NULL,
    department_id INT,
    CONSTRAINT fk_department FOREIGN KEY (department_id) REFERENCES departments(department_id)
);

CREATE TABLE enrollments (
    enrollment_id SERIAL PRIMARY KEY,
    student_id INT,
    course_name VARCHAR(100) NOT NULL,
    semester VARCHAR(50) NOT NULL,
    enrollment_date DATE,
    CONSTRAINT fk_student FOREIGN KEY (student_id) REFERENCES students(student_id)
);
