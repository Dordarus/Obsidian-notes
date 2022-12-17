-   BCNF rules
-   Should not have [[Multivalued Dependency]]

### Problem 

| Course ID | Student ID | Grade |
|-----------|------------|-------|
| CSC101    | 1          | A     |
| CSC101    | 1          | B     |
| CSC101    | 2          | A     |
| CSC202    | 1          | B     |
| CSC202    | 3          | C     |

In this table, the multivalued dependency "Course ID, Student ID -> Grade" holds because, for each combination of "Course ID" and "Student ID" values, there is a corresponding "Grade" value.

### In 4NF

In order to represent the multivalued dependency "Course ID, Student ID -> Grade" in 4th normal form (4NF), we need to decompose the table into two separate tables: one for courses and one for students. Here is an example of how this could be done:

	Courses table:

| Course ID | Course Name          |
|-----------|----------------------|
| CSC101    | Computer Science 101 |
| CSC202    | Computer Science 202 |

	Students table:

| Student ID | Student Name | Course ID | Grade |
|------------|--------------|-----------|-------|
| 1          | John Smith   | CSC101    | A     |
| 1          | John Smith   | CSC101    | B     |
| 1          | John Smith   | CSC202    | B     |
| 2          | Jane Doe     | CSC101    | A     |
| 3          | Bob Johnson  | CSC202    | C     |

In this design, the multivalued dependency "Course ID, Student ID -> Grade" is represented by the foreign key "Course ID" in the "Students" table, which refers to the "Course ID" in the "Courses" table. This design satisfies the requirements of 4NF because there are no non-trivial multivalued dependencies in either table.