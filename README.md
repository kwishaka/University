# University Course Registration and Academic Management System
 
**Student:** ukwishaka sandrine  **Registration No.:** 27672

**Scope:** Model and Repository layers

## Tech stack

| Category | Technology |
|---|---|
| Language | Java 21 (17+ required) |
| Framework | Spring Boot 3.5.7 (Spring Initializr) |
| ORM | Spring Data JPA / Hibernate 6 |
| Database | PostgreSQL, database `university_academic_db` |
| Build tool | Maven |
| Version control | Git and GitHub |

## Entities

Department, Student, StudentProfile, Lecturer, Course, Registration.

| Relationship | Type | Implementation |
|---|---|---|
| Department – Course | 1 : N | FK `department_id` in courses |
| Department – Lecturer (employs) | 1 : N | FK `department_id` in lecturers |
| Department – Lecturer (head) | 1 : 1 | FK `head_id` (unique) in departments |
| Department – Student | 1 : N | FK `department_id` in students |
| Student – StudentProfile | 1 : 1 | FK `student_id` (unique) in student_profiles |
| Lecturer – Course | M : N | Join table `lecturer_courses` (no entity) |
| Student – Course | M : N | Join entity `Registration` |


## Repository contents

| Deliverable | Location |
|---|---|
| 1. Problem analysis and identified entities | [`docs/analysis.md`](docs/analysis.md) |
| 2. Entity Relationship Diagram | [`docs/erd.png`](docs/erd.png), [`docs/erd.md`](docs/erd.md) |
| 3. Relational database schema | [`docs/schema.md`](docs/schema.md) |
| 4. Spring Boot source code | [`src/`](src/) (`model` and `repository` packages) |
| 5. PostgreSQL database (generated tables) | [`database/university_academic_db.sql`](database/university_academic_db.sql) |
| 6. Screenshots | [`docs/screenshots/`](docs/screenshots/) |

## How to run

1. Install Java 17+, Maven and PostgreSQL.
2. Create the database:
   ```sql
   CREATE DATABASE university_academic_db;
   ```
3. Set your credentials in `src/main/resources/application.properties`:
   ```properties
   spring.datasource.url=jdbc:postgresql://localhost:5432/university_academic_db
   spring.datasource.username=postgres
   spring.datasource.password=YOUR_PASSWORD
   spring.jpa.hibernate.ddl-auto=update
   spring.jpa.show-sql=true
   ```
4. Run the application:
   ```bash
   mvn spring-boot:run
   ```
5. Hibernate generates all seven tables automatically. Check them in pgAdmin.
