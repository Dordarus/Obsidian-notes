In database design, a join dependency is a relationship between attributes in a table such that the table can be decomposed into two or more smaller tables that can be joined back together to reconstruct the original table.

For example, consider a table with the following attributes: "Course ID," "Course Name," "Student ID," and "Student Name." This table has a join dependency if it can be decomposed into two smaller tables, such as a "Courses" table and a "Students" table, that can be joined back together to reconstruct the original table. 

| Course ID | Course Name          | Student ID | Student Name | 
|-----------|----------------------|------------|--------------|
| CSC101    | Computer Science 101 | 1          | John Smith   |
| CSC101    | Computer Science 202 | 2          | Jane Doe     |
| CSC202    | Computer Science 101 | 3          | Bob Johnson  |

The resulting tables might look like this:

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

>[!NOTE]
>However, it is important to note that tables with join dependencies may not always be in 3rd normal form (3NF). To be in 3NF, a table must not only satisfy the requirements of 1NF and 2NF, but it must also not have any non-trivial join dependencies. Therefore, it may be necessary to further decompose tables with join dependencies in order to bring them into 3NF.