-   2NF rules
-   Should not have [[Transitive Dependency]]

### Problem 

| EmployeeID | LastName | FirstName | Department | Manager |
|------------|----------|-----------|------------|---------|
| 1          | Smith    | John      | Marketing   | 2       |
| 2          | Johnson  | Mary      | Sales       | 3       |
| 3          | Williams | Bill      | Finance     |         |

In this table, the `Manager` attribute is transitively dependent on the `EmployeeID` attribute, because it depends on the `LastName` attribute, which in turn depends on the `EmployeeID` attribute. This means that the `Manager` attribute is indirectly dependent on the primary key (`EmployeeID`).

### In 3NF

To eliminate the transitive dependency, we can create a separate table for the `Manager` attribute, and include the `EmployeeID` attribute as a foreign key. This will ensure that the `Manager` attribute is independent of the other non-key attributes, and the table will be in third normal form.

	Employee Table:

| EmployeeID | LastName | FirstName | Department |
|------------|----------|-----------|------------|
| 1          | Smith    | John      | Marketing   |
| 2          | Johnson  | Mary      | Sales       |
| 3          | Williams | Bill      | Finance     |

	Manager Table:

| EmployeeID | Manager |
|------------|---------|
| 1          | 2       |
| 2          | 3       |

>[!INFO] Also read
> - [[Boyce-Codd Normal Form]]
> - [[Fourth Normal Form]]
