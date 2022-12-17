The Boyce-Codd Normal Form (BCNF) is a database normal form that is used to eliminate certain types of functional dependencies in a database table. It is named after Raymond F. Boyce and Edgar F. Codd, who independently developed the concept in the 1970s.

BCNF is a stricter version of third normal form (3NF), and is designed to eliminate certain types of functional dependencies that are not addressed by 3NF. In particular, BCNF is designed to eliminate non-trivial functional dependencies on non-key attributes.

-   3NF rules
-   It has no [[Non-trivial functional dependency|non-trivial functional dependencies]] on any non-key attribute.

### Problem

| CustomerID | CustomerName | CustomerAddress | CustomerPhone | OrderID | OrderDate |
|------------|--------------|-----------------|---------------|---------|-----------|
| 1          | John Smith   | 123 Main St     | 555-555-1212 | 1001    | 2021-01-01 |
| 2          | Mary Johnson | 456 Park Ave    | 555-555-1213 | 1002    | 2021-01-02 |
| 3          | Bill Williams| 789 Maple St    | 555-555-1214 | 1003    | 2021-01-03 |

In this table, the `OrderID` attribute is functionally dependent on the `CustomerID` attribute, because the value of `OrderID` is uniquely determined by the value of `CustomerID`. However, the `OrderDate` attribute is functionally dependent on the `OrderID` attribute, because the value of `OrderDate` is uniquely determined by the value of `OrderID`. This means that the `OrderDate` attribute is transitively dependent on the `CustomerID` attribute.

### In BCNF

To eliminate the transitive dependency, we can create a separate table for the `Order` attribute, and include the `CustomerID` and `OrderID` attributes as foreign keys. This will ensure that the `OrderDate` attribute is independent of the other non-key attributes, and the table will be in BCNF.

	Customer Table:

| CustomerID | CustomerName | CustomerAddress | CustomerPhone |
|------------|--------------|-----------------|---------------|
| 1          | John Smith   | 123 Main St     | 555-555-1212 |
| 2          | Mary Johnson | 456 Park Ave    | 555-555-1213 |
| 3          | Bill Williams| 789 Maple St    | 555-555-1214 |

	Order Table:

| CustomerID | OrderID | OrderDate |
|------------|---------|-----------|
| 1          | 1001    | 2021-01-01 |
| 2          | 1002    | 2021-01-02 |
| 3          | 1003    | 2021-01-03 |

>[!INFO] Also read
> - [[Fourth Normal Form]]
