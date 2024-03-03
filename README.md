# SQL_Join

Students Table

```
CREATE TABLE Students (
    student_id INT PRIMARY KEY,
    student_name VARCHAR(100),
    department_id INT,
    FOREIGN KEY (department_id) REFERENCES Departments(department_id)
);
```

Courses table

```
CREATE TABLE Courses (
    course_id INT PRIMARY KEY,
    course_name VARCHAR(100),
    department_id INT,
    FOREIGN KEY (department_id) REFERENCES Departments(department_id)
);
```


Enrollments Table

```
CREATE TABLE Enrollments (
    enrollment_id INT PRIMARY KEY,
    student_id INT,
    course_id INT,
    FOREIGN KEY (student_id) REFERENCES Students(student_id),
    FOREIGN KEY (course_id) REFERENCES Courses(course_id)
);
```

```
CREATE TABLE Instructors (
    instructor_id INT PRIMARY KEY,
    instructor_name VARCHAR(100),
    department_id INT,
    FOREIGN KEY (department_id) REFERENCES Departments(department_id)
);
```


```
CREATE TABLE Departments (
    department_id INT PRIMARY KEY,
    department_name VARCHAR(100)
);
```



# Insert Into Tables

Departments

```
INSERT INTO Departments VALUES 
(1, 'Computer Science'), 
(2, 'Mathematics'),
(3, 'Engineering');
```


Students

```
INSERT INTO Students VALUES 
(1, 'John Doe', 1),
(2, 'Jane Smith', 2),
(3, 'Alice Johnson', 3),
(4, 'Chris Martin', 1), -- Not enrolled in any course
(5, 'Brian Clark', 2); -- Not enrolled in any course
```

Courses

```
INSERT INTO Courses VALUES 
(101, 'Intro to Computer Science', 1),
(102, 'Calculus', 2),
(103, 'Engineering Basics', 3),
(104, 'Advanced Mathematics', 2); -- No students enrolled
```


Enrollment

```
INSERT INTO Enrollments VALUES 
(1001, 1, 101),
(1002, 2, 102),
(1003, 3, 103);
```


Instructors

```
INSERT INTO Instructors VALUES 
(201, 'Dr. Alice', 1),
(202, 'Prof. Bob', 2),
(203, 'Dr. Charles', 3);
```



## Inner Join


 INNER JOIN
Query: Match students with their primary course of interest.

```
SELECT S.student_name, C.course_name
FROM Students S
INNER JOIN Courses C ON S.primary_course_id = C.course_id;
```


##  LEFT JOIN
Query: List all students and their primary course of interest, including those without one.


```
SELECT S.student_name, C.course_name
FROM Students S
LEFT JOIN Courses C ON S.primary_course_id = C.course_id;
```


## RIGHT JOIN
Query: List all courses and any students who have them as their primary interest.

```
SELECT S.student_name, C.course_name
FROM Courses C
LEFT JOIN Students S ON C.course_id = S.primary_course_id;
```


