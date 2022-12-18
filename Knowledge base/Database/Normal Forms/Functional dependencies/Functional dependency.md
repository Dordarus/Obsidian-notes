In database design, a functional dependency is a relationship between two attributes in a database table that specifies that the value of one attribute (the dependent attribute) is uniquely determined by the value of another attribute (the determinant attribute).

For example, consider the following table:

| EmployeeID | LastName | FirstName | Department |
|------------|----------|-----------|------------|
| 1          | Smith    | John      | Marketing   |
| 2          | Johnson  | Mary      | Sales       |
| 3          | Williams | Bill      | Finance     |

In this table, the `LastName` attribute is functionally dependent on the `EmployeeID` attribute, because the value of `LastName` is uniquely determined by the value of `EmployeeID`. This means that for each value of `EmployeeID`, there is only one corresponding value of `LastName`.

Functional dependencies are important in database design because they can help to identify the relationships between different attributes in a table, and they can be used to ensure data integrity and data consistency. For example, if a functional dependency is specified between two attributes, it can be used to ensure that any changes to the value of the determinant attribute are automatically reflected in the value of the dependent attribute.

Functional dependencies can also be used to identify the primary [[DBMS key|key]] of a table, which is a set of attributes that uniquely identifies each row in the table. In the example above, the combination of `EmployeeID` and `Department` is the primary key of the table, because each combination of `EmployeeID` and `Department` values corresponds to a unique row in the table.