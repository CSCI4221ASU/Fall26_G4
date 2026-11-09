Malachi Johnson

# Project 4: Software Architecture
## Final Grade Calculator

Course: CSCI 4221
Group: 4
Team Members: Malachi Johnson and Jalen Davis
Sprint: 4
My Component: Course Management
My Database Table: Courses

This document describes our proposed application design. The files listed below are planned files for development.

# Section 1: Description of Our Container

## Application Architecture

Our Final Grade Calculator will be a cloud-based application. Students will access it through a web browser to enter course information and assignment grades. The application will calculate current grades and the scores needed on final exams.

Software architecture describes how the main parts of an application are organized and how they work together. Three common architecture patterns are layered architecture and client-server architecture and Model-View-Controller.

Our application will use three layers:

- Presentation layer: HTML and CSS and JavaScript will provide the screens students use.
- Application layer: Java and Spring Boot will handle requests and course management and grade calculations.
- Data layer: A shared MySQL database will store courses and assignments.

The browser will send requests to the Spring Boot application. The application will process each request and access MySQL when stored information is needed. It will then return a result to the browser.

## Docker and Our Container

Docker is a platform for building and running containers. A container is an isolated environment that runs an application with the resources it needs.

Our application container will include:

- A Java runtime.
- The Maven-built Spring Boot application JAR.
- Required libraries packaged with the application.
- HTML and CSS and JavaScript files packaged with the application.
- Application configuration.

The container will run the backend and serve the frontend files. MySQL will run separately from the application container. Both team members' components will use the same database through the backend.

Database credentials will be supplied through environment variables. They will not be written into the Docker image.

## Docker Image and Daemon

A Docker image is the packaged template used to create a container. Our image will contain the Java runtime and the built application.

The Docker daemon is the background service that manages images and containers and networks and volumes on the host computer. It runs outside our application container.

## Container Files

| File | Purpose |
|---|---|
| Dockerfile | Defines how to build the application image and start the application. |
| pom.xml | Defines dependencies and Maven build settings. |
| docker-compose.yml | Defines the application and MySQL services for local testing. |
| application.properties | Defines application settings and reads database connection values from environment variables. |
| .dockerignore | Keeps unnecessary local files out of the image build context. |

For cloud deployment the application container will connect to a separate MySQL service. Database storage must remain available when the application container is replaced.

# Section 2: Components and Necessary Files

## Major Components

| Component | Responsibility |
|---|---|
| User Interface | Allows students to enter information and view results. |
| Course Management | Creates and updates courses and manages their related assignment information. |
| Grade Calculation | Calculates current grades and required final exam scores and estimated final grades. |
| Database | Stores course and assignment records in shared MySQL tables. |

Jalen Davis is responsible for Grade Calculation and the Assignments table. I am responsible for Course Management and the Courses table. We will work together on the interface and Docker setup and database integration.

## My Component: Course Management

The Course Management Component will organize the courses entered by students. It will let students add a course and view saved courses and update course details and remove a course.

Its subcomponents are:

- Course creation.
- Course information management.
- Assignment management within a course.
- Grading category management.
- Input validation.

Grading categories will use the category information associated with assignments. Our initial design does not include a separate category table.

## Necessary Files

| File | Purpose |
|---|---|
| Course.java | Represents a course with its ID and name and code and credit hours. |
| Assignment.java | Represents an assignment linked to a course. This model is shared with Jalen's component. |
| CourseController.java | Receives course requests from the browser and returns responses. |
| CourseService.java | Validates course information and handles course operations. |
| CourseRepository.java | Reads and saves course records in MySQL. |
| AssignmentRepository.java | Accesses assignments associated with a course. |
| index.html | Provides the course entry form and saved course display. |
| style.css | Controls the appearance of the interface. |
| script.js | Sends requests to the backend and updates the page. |
| application.properties | Provides application and database configuration. |

## How the Component Works

When a student adds a course the browser sends the entered information to CourseController. The controller passes it to CourseService for validation. CourseService uses CourseRepository to save the course in MySQL.

The application will require a course name and course code. Credit hours must be a positive whole number. The database will generate the course ID.

The same request flow will support viewing and updating courses. Before deleting a course the service will check for related assignments. In this initial design a course with assignments must have those assignments removed before the course can be deleted.

## Database Usage

Course Management will use a shared database rather than a separate local database for each component. The frontend will communicate with the backend instead of connecting directly to MySQL.

CourseRepository will access the Courses table. AssignmentRepository will retrieve assignments belonging to a selected course. Jalen's Grade Calculation Component will use those assignment records to calculate results.

# Section 3: Structure of the Related Database Table

## Courses Table

The Courses table will store one record for each course.

| Column | Data Type | Constraint | Purpose |
|---|---|---|---|
| course_id | INT | Primary key and auto increment | Identifies each course. |
| course_name | VARCHAR(100) | NOT NULL | Stores the course name. |
| course_code | VARCHAR(20) | NOT NULL | Stores the course code. |
| credit_hours | INT | NOT NULL | Stores the number of credit hours. |

The primary key prevents two course records from having the same ID. Required fields must contain a value before a record can be saved. The service will reject blank names and codes and credit hours below 1.

## Proposed SQL Definition

CREATE TABLE Courses (
    course_id INT AUTO_INCREMENT PRIMARY KEY,
    course_name VARCHAR(100) NOT NULL,
    course_code VARCHAR(20) NOT NULL,
    credit_hours INT NOT NULL,
    CONSTRAINT chk_course_credit_hours CHECK (credit_hours > 0)
);

## Relationship to Jalen's Assignments Table

One course can have many assignments. Each assignment belongs to one course.

The course_id column in Jalen's Assignments table will reference Courses.course_id as a foreign key. Both columns will use the INT data type.

Jalen's table will contain:

- assignment_id
- course_id
- assignment_name
- category
- weight
- score
- max_score

This relationship allows the application to retrieve assignments for a selected course and pass their scores and weights to the Grade Calculation Component.

## Example Course Record

| course_id | course_name | course_code | credit_hours |
|---|---|---|---|
| 1 | Software Engineering | CSCI 4221 | 3 |

Assignments connected to this example course will store 1 in their course_id field.

The Courses table will organize course information while the Assignments table will store the grade information used for calculations.