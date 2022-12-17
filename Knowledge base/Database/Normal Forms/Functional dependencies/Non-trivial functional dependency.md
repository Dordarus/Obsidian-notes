In database design, a functional dependency is a relationship between two attributes in a table such that the value of one attribute determines the value of the other attribute. For example, if a table has attributes "Employee ID" and "Employee Name," the functional dependency would be "Employee ID -> Employee Name," meaning that the value of the "Employee ID" attribute uniquely determines the value of the "Employee Name" attribute.

A non-trivial functional dependency is a functional dependency that does not involve an attribute determining itself. 

| Employee ID | Employee Name |
|-------------|---------------|
| 1           | John Smith    |
| 2           | Jane Doe      |
| 3           | Bob Johnson   |

In this table, the functional dependency "Employee ID -> Employee Name" is non-trivial because "Employee ID" determines a value that is different from itself. The functional dependency "Employee Name -> Employee ID" is not considered non-trivial because "Employee Name" determines itself.

>[!NOTE]
>Non-trivial functional dependencies are important in database design because they can help ensure the integrity and correctness of data in the database. By identifying and enforcing these dependencies, it is possible to ensure that data is accurately and consistently represented in the database, which can help prevent errors and improve the overall quality of the database.