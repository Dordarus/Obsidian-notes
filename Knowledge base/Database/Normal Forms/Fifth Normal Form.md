also known as PJNF (Project Join Normal Form)

-   NF4 rules
-   Should not have [[Join Dependency]]

5th normal form (5NF) is a higher level of database normalization that is designed to eliminate redundant data and improve the overall integrity and quality of a database.

To be in 5NF, a table must satisfy the requirements of all lower normal forms (1NF, 2NF, 3NF, and 4NF) and must not have any non-trivial join dependencies. In addition, a table in 5NF must not have any non-trivial multivalued dependencies.

A multivalued dependency is a relationship between three or more attributes in a table such that the presence of certain combinations of values in the attributes implies the presence of certain other combinations of values in the attributes. For example, consider a table with the following attributes: "Course ID," "Student ID," and "Grade." The multivalued dependency "Course ID, Student ID -> Grade" states that, given a course ID and a student ID, we can determine the grade that the student received in that course.

To be in 5NF, a table must not have any non-trivial multivalued dependencies. This means that, for any set of attributes in the table, there must not be any non-trivial functional dependencies among the attributes in that set.

Problem

| Course ID | Course Name          | Student ID | Student Name | 
|-----------|----------------------|------------|--------------|
| CSC101    | Computer Science 101 | 1          | John Smith   |
| CSC101    | Computer Science 101 | 2          | Jane Doe     |
| CSC202    | Computer Science 202 | 1          | John Smith   |
| CSC202    | Computer Science 202 | 3          | Bob Johnson  |

This table has a non-trivial join dependency because it can be decomposed into two smaller tables that can be joined back together to reconstruct the original table. The resulting tables might look like this:

	Courses table:

| Course ID | Course Name          |
|-----------|----------------------|
| CSC101    | Computer Science 101 |
| CSC202    | Computer Science 202 |

	Students table:

| Student ID | Student Name | Course ID |
|------------|--------------|-----------|
| 1          | John Smith   | CSC101    |
| 2          | Jane Doe     | CSC101    |
| 1          | John Smith   | CSC202    |
| 3          | Bob Johnson  | CSC202    |

In this design, the join dependency is represented by the foreign key "Course ID" in the "Students" table, which refers to the "Course ID" in the "Courses" table.

## In 5NF

To bring the previous example into 5th normal form (5NF), we need to eliminate the non-trivial join dependency. This can be done by further decomposing the tables into smaller tables that do not have any join dependencies.

Here is an example of how this could be done:

	Courses table:

| Course ID | Course Name          |
|-----------|----------------------|
| CSC101    | Computer Science 101 |
| CSC202    | Computer Science 202 |

	Students table:

| Student ID | Student Name | Course ID |
|------------|--------------|-----------|
| 1          | John Smith   | CSC101    |
| 2          | Jane Doe     | CSC101    |
| 3          | Bob Johnson  | CSC202    |

	Enrollments table:

| Course ID | Student ID |
|-----------|------------|
| CSC101    | 1          |
| CSC101    | 2          |
| CSC202    | 1          |
| CSC202    | 3          |

In this design, the original table has been decomposed into three smaller tables: "Courses," "Students," and "Enrollments." The "Enrollments" table represents the relationship between courses and students, and it does not have any join dependencies.

This design satisfies the requirements of 5NF because there are no non-trivial multivalued dependencies or non-trivial join dependencies in any of the tables.