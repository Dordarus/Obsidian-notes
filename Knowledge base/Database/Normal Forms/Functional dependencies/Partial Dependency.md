In database design, a partial dependency is a type of [[Functional dependency|functional dependency]] in which an attribute depends on a part of a composite primary key, rather than the entire key. For example, consider the following table:

| EmployeeID | LastName | FirstName | Department |
|------------|----------|-----------|------------|
| 1          | Smith    | John      | Marketing   |
| 2          | Johnson  | Mary      | Sales       |
| 3          | Williams | Bill      | Finance     |

In this table, the primary key is composed of both the `EmployeeID` and `Department` attributes. If we consider the `LastName` attribute, it is partially dependent on the primary key, because it depends on the `EmployeeID` attribute but not the `Department` attribute. This means that the `LastName` attribute is dependent on only a part of the primary key.

Partial dependencies can cause problems in a database because they can lead to data redundancy and data inconsistencies. For example, if the `LastName` attribute is partially dependent on the primary key, it could be stored multiple times in the table, resulting in data redundancy. This can lead to data inconsistencies, because if the `LastName` attribute is updated in one place, it may not be updated in all the other places where it is stored.

>[!NOTE]
>To eliminate partial dependencies, a table should be designed so that all non-key attributes are fully dependent on the entire primary key. This is one of the criteria for a table to be in second normal form ([[Second Normal Form|2NF]]).