In database design, a transitive dependency is a type of functional dependency in which an attribute depends on another attribute that is not the primary key.

For example, consider the following table:

| EmployeeID | LastName | FirstName | Department | Manager |
|------------|----------|-----------|------------|---------|
| 1          | Smith    | John      | Marketing   | 2       |
| 2          | Johnson  | Mary      | Sales       | 3       |
| 3          | Williams | Bill      | Finance     |         |

In this table, the `Manager` attribute is transitively dependent on the `EmployeeID` attribute, because it depends on the `LastName` attribute, which in turn depends on the `EmployeeID` attribute. This means that the `Manager` attribute is indirectly dependent on the primary key (`EmployeeID`).

Transitive dependencies can cause problems in a database because they can lead to data redundancy and data inconsistencies. For example, if the `Manager` attribute is transitively dependent on the primary key, it could be stored multiple times in the table, resulting in data redundancy. This can lead to data inconsistencies, because if the `Manager` attribute is updated in one place, it may not be updated in all the other places where it is stored.

>[!NOTE]
>To eliminate transitive dependencies, a table should be designed so that all non-key attributes are independent of each other. This is one of the criteria for a table to be in third normal form ([[Third Normal Form|3NF]]).