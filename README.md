# Internship Candidate Finder

A Java-based console application for managing universities, courses, and students, designed to help organizations efficiently search for internship candidates based on location and academic criteria. The project uses MySQL for persistent data storage and JDBC for database connectivity.

---

## Features

- **Add Students, Courses, and Universities:**  
  Easily input and store academic data.

- **Search for Internship Candidates:**  
  Find students by state, city, and course/area.

- **Remove Students or Remove Students from Courses:**  
  Delete student records or remove students from specific courses.

- **Database Integration:**  
  All data is stored and managed in a MySQL database.

---

## Technologies Used

- **Java 8+**
- **MySQL Server**
- **JDBC (MySQL Connector/J)**
- **VS Code (recommended IDE)**

---

## Setup Instructions

### 1. Prerequisites

- [Java JDK 8 or higher](https://adoptopenjdk.net/)
- [MySQL Server](https://dev.mysql.com/downloads/mysql/)
- [MySQL Connector/J](https://dev.mysql.com/downloads/connector/j/)

### 2. Database Setup

1. **Start MySQL Server** and log in:
   ```sh
   mysql -u root -p
   ```

2. **Create the database:**
   ```sql
   CREATE DATABASE internship_finder_new2;
   USE internship_finder_new2;
   ```

3. **Create required tables:**
   ```sql
   CREATE TABLE universities (
       id INT AUTO_INCREMENT PRIMARY KEY,
       name VARCHAR(255),
       address VARCHAR(255),
       district VARCHAR(255),
       city VARCHAR(255),
       state VARCHAR(255)
   );

   CREATE TABLE courses (
       id INT AUTO_INCREMENT PRIMARY KEY,
       name VARCHAR(255),
       acronym VARCHAR(50),
       area VARCHAR(255)
   );

   CREATE TABLE university_courses (
       university_id INT,
       course_id INT,
       FOREIGN KEY (university_id) REFERENCES universities(id),
       FOREIGN KEY (course_id) REFERENCES courses(id)
   );

   CREATE TABLE students (
       id INT AUTO_INCREMENT PRIMARY KEY,
       name VARCHAR(255),
       enrollment VARCHAR(50),
       date_of_birth DATE,
       year_of_enrollment INT,
       situation VARCHAR(255)
   );

   CREATE TABLE course_students (
       course_id INT,
       student_id INT,
       FOREIGN KEY (course_id) REFERENCES courses(id),
       FOREIGN KEY (student_id) REFERENCES students(id)
   );
   ```

### 3. Project Configuration

- Place the MySQL Connector/J JAR file in a known location.
- Ensure `.vscode/settings.json` references the connector:
  ```json
  "java.project.referencedLibraries": [
      "lib/**/*.jar",
      "C:\\Users\\91950\\Downloads\\mysql-connector-j-9.4.0\\mysql-connector-j-9.4.0\\mysql-connector-j-9.4.0.jar"
  ]
  ```

### 4. Running the Application

#### Using VS Code

- Open the project folder in VS Code.
- Compile and run `Main.java` using the Java extension pack.

#### Using Command Line

```sh
javac -cp ".;C:\path\to\mysql-connector-j-9.4.0.jar" src\Main.java
java -cp ".;src;C:\path\to\mysql-connector-j-9.4.0.jar" Main
```

---

## Usage

- The application runs in the terminal and presents a menu:
  - Add Student
  - Add Course
  - Add University
  - Search for Students
  - Remove Student
  - Remove Student from Course
  - Exit

- Follow prompts to enter data or search for candidates.

---

## Troubleshooting

- **Database Connection Errors:**  
  Ensure your MySQL username, password, and database name in `Main.java` match your MySQL setup.

- **JDBC Driver Not Found:**  
  Confirm the connector JAR path is correct in `.vscode/settings.json` or your classpath.

---

## License

This project is for educational and demonstration purposes.

---

## Author

Developed by Gaurav Jadhav.  
For questions or support,