## Rules for Second Normal Form

-   1NF rules
-   There should be no [[Partial Dependency]]

### Problem 

| EmployeeID | LastName | FirstName | Department |
|------------|----------|-----------|------------|
| 1          | Smith    | John      | Marketing   |
| 2          | Johnson  | Mary      | Sales       |
| 3          | Williams | Bill      | Finance     |

In this table, the primary key is composed of both the `EmployeeID` and `Department` attributes. The `LastName` attribute is partially dependent on the primary key, because it depends on the `EmployeeID` attribute but not the `Department` attribute.

### In 2NF

To eliminate the partial dependency, we can create a separate table for the `LastName` attribute, and include the `EmployeeID` attribute as a foreign key. This will ensure that the `LastName` attribute is fully dependent on the primary key, and the table will be in second normal form.

	Employee Table:

| EmployeeID | FirstName | Department |
|------------|-----------|------------|
| 1          | John      | Marketing   |
| 2          | Mary      | Sales       |
| 3          | Bill      | Finance     |

	LastName Table:

| EmployeeID | LastName |
|------------|----------|
| 1          | Smith    |
| 2          | Johnson  |
| 3          | Williams |