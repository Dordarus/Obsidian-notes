In database design, a multivalued dependency is a relationship between three or more attributes in a table such that the presence of certain combinations of values in the attributes implies the presence of certain other combinations of values in the attributes.

For example, consider a table with the following attributes: "Course ID," "Student ID," and "Grade." The functional dependency "Course ID -> Grade" represents the fact that each course has a set of grades associated with it. However, this functional dependency does not capture the fact that each student can have multiple grades in a course. To represent this relationship, we can use the multivalued dependency "Course ID, Student ID -> Grade." This dependency states that, given a course ID and a student ID, we can determine the grade that the student received in that course.

Here is an example table that illustrates this multivalued dependency:

| Course ID | Student ID | Grade |
|-----------|------------|-------|
| CSC101    | 1          | A     |
| CSC101    | 1          | B     |
| CSC101    | 2          | A     |
| CSC202    | 1          | B     |
| CSC202    | 3          | C     |

In this table, the multivalued dependency "Course ID, Student ID -> Grade" holds because, for each combination of "Course ID" and "Student ID" values, there is a corresponding "Grade" value.