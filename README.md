Student Management REST API

A Spring Boot REST API for managing student records, built as an assignment for Project Based Learning in Java at Chandigarh University. It supports full CRUD operations on students and filtering students by course, backed by a PostgreSQL database.

Author: Shyam Bihari Yadav (24BCS12310) Submitted to: Er. Deep Prakash Section: 24BCS-KRG-617A

Tech Stack
Java
Spring Boot (Spring Web, Spring Data JPA)
Hibernate ORM
PostgreSQL
Maven
Postman (API testing)
Features
Add a new student
Retrieve all students
Retrieve a student by ID
Update student details
Delete a student
Filter students by course
Project Structure
student-management-api/
├── src/
│   ├── main/
│   │   ├── java/com/example/demo/
│   │   │   ├── DemoApplication.java
│   │   │   ├── controller/
│   │   │   │   └── StudentController.java
│   │   │   ├── service/
│   │   │   │   ├── StudentService.java
│   │   │   │   └── StudentServiceImpl.java
│   │   │   ├── repository/
│   │   │   │   └── StudentRepository.java
│   │   │   └── entity/
│   │   │       └── Student.java
│   │   └── resources/
│   │       └── application.properties
│   └── test/
├── screenshots/
├── README.md
├── .gitignore
└── pom.xml
Student Entity
Attribute	Description
id	Primary key (auto-generated)
name	Student name
email	Student email address
course	Enrolled course
age	Student age
Getting Started
Prerequisites
JDK (version as set in pom.xml)
Maven
PostgreSQL
1. Clone the repository
bash
git clone https://github.com/Shyam091/PBLJ_Assignment.git
cd PBLJ_Assignment
2. Create the database
sql
CREATE DATABASE student_db;
3. Configure the application

Open src/main/resources/application.properties and set your own PostgreSQL username and password:

properties
server.port=8081

spring.datasource.url=jdbc:postgresql://localhost:5432/student_db
spring.datasource.username=<your-db-username>
spring.datasource.password=<your-db-password>
spring.datasource.driver-class-name=org.postgresql.Driver

spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true
spring.jpa.database-platform=org.hibernate.dialect.PostgreSQLDialect

Never commit real credentials to GitHub. Keep your local password out of version control.

4. Run the application
bash
mvn spring-boot:run

The API starts at http://localhost:8081.

API Endpoints

Base URL: http://localhost:8081

HTTP Method	Endpoint	Description
POST	/api/students	Add a new student
GET	/api/students	Retrieve all students
GET	/api/students/{id}	Retrieve student by ID
PUT	/api/students/{id}	Update student details
DELETE	/api/students/{id}	Delete a student
GET	/api/students/course/{course}	Retrieve students by course
Example request body (POST and PUT)
json
{
  "name": "Sample Student",
  "email": "student@example.com",
  "course": "Java",
  "age": 21
}

For POST, the database generates the id. For PUT, the request body contains the replacement values.

Example requests
bash
# Add a student
curl -X POST http://localhost:8081/api/students \
  -H "Content-Type: application/json" \
  -d '{"name":"Test 1","email":"abc@gmail.com","course":"CSE","age":21}'

# Get all students
curl http://localhost:8081/api/students

# Get student by ID
curl http://localhost:8081/api/students/1

# Update a student
curl -X PUT http://localhost:8081/api/students/1 \
  -H "Content-Type: application/json" \
  -d '{"name":"Test 0","email":"xyz@gmail.com","course":"CSE","age":22}'

# Delete a student
curl -X DELETE http://localhost:8081/api/students/1

# Filter by course
curl http://localhost:8081/api/students/course/CSE
API Testing

All endpoints were tested using Postman. Screenshots of each request and response (add, get all, get by ID, update, delete, filter by course) are included in the project report and the screenshots/ folder.

License

This project was created for academic purposes.
