In a database management system (DBMS), a key is a field or set of fields in a table that uniquely identifies each row in the table. There are several types of keys that can be used in a DBMS, including:

| Sid | SName | SBranch     | SEmail        |
|-----|-------|-------------|---------------|
| 1   | John  | C.S.        | `john@xyz.com`  |
| 2   | Adam  | C.S.        | `adam1@xyz.com` |
| 3   | Adam  | I.T.        | `adam2@xyz.com` |
| 4   | Elly  | Electronics | `elly@xyz.com`  |

``SId`` column has unique value for all the rows of data and the `SEmail` column also has unique email addresses and these two columns can be used to identify the course in the above table so we can say that `SId` and `SEmail` are keys for this relation.

DBMS keys serve several important functions in a database management system. Some of the main reasons why keys are used in a DBMS include:

1. **To uniquely identify each row in a table**: A primary key is used to uniquely identify each row in a table. This is important because it allows the DBMS to easily locate and manipulate specific rows in the table.
2. **To establish relationships between tables**: Foreign keys are used to establish relationships between tables. For example, a foreign key in one table may refer to the primary key of another table, indicating that the two tables are related in some way.
3. **To enforce data integrity**: Keys can be used to enforce data integrity by preventing the insertion of duplicate values or null values into the key field.
4. **To improve database performance**: Using keys to uniquely identify rows in a table can improve the performance of database queries, since the DBMS can use the keys to quickly locate the relevant rows.

Overall, keys play a crucial role in ensuring the accuracy, integrity, and performance of a database management system.

1. [[#Super key]]: This is a set of one or more fields in a table that can uniquely identify each row in the table. It may consist of a single field (such as a primary key) or multiple fields. A super key can include both natural keys (fields that already exist in the table) and artificial keys (fields that are created specifically for the purpose of identifying rows in the table).

2. [[#Natural key]]: This is a field or set of fields that already exists in the table and can be used as the primary key. Natural keys are often preferred to surrogate keys because they are more meaningful and can provide additional context about the data in the table.

3. [[#Alternate key]]: This is a field or set of fields in a table that could be used as a primary key, but is not currently being used as the primary key. A table can have one or more alternate keys, in addition to its primary key.

3. [[#Candidate key]]: This is a field or set of fields that could potentially be used as a primary key. A table may have one or more candidate keys, but only one of them can be chosen as the primary key.

4. [[#Surrogate key]]: This is a synthetic key that is created by the DBMS and used as a primary key. It is often used when it is not possible to use a natural key (a field or set of fields that already exists in the table) as the primary key.

5. [[#Composite key]]: This is a key that is made up of two or more fields in a table. It is used when a single field is not sufficient to uniquely identify a row in the table.

6. [[#Primary Key]]: This is a unique identifier for each row in the table. It cannot contain null values and must be unique for each row.

7. [[#Foreign key]]: This is a field that refers to the primary key of another table. It is used to establish a relationship between two tables and to enforce referential integrity.

## Super key

| EmployeeID | Name          | Age | Gender | SocialSecurityNumber | EmailAddress        |
|------------|---------------|-----|--------|----------------------|---------------------|
| 1          | John Doe      | 32   | Male   | 123-45-6789          | `johndoe@example.com` |
| 2          | Jane Smith    | 28   | Female | 234-56-7890          | `janesmith@example.com` |
| 3          | Robert Johnson | 45   | Male   | 345-67-8901          | `rjohnson@example.com` |

In this table, the super key consists of the combination of the `EmployeeID`, `SocialSecurityNumber`, and `EmailAddress` fields. This means that any combination of these three fields would be sufficient to uniquely identify each row in the table.

However, the primary key for this table is just the `EmployeeID` field. This means that the `EmployeeID` field is the field that is currently being used to uniquely identify each row in the table.

## Composite key

| EmployeeID | Name          | Age | Gender | SocialSecurityNumber | EmailAddress        | Department |
|------------|---------------|-----|--------|----------------------|---------------------|------------|
| 1          | John Doe      | 32   | Male   | 123-45-6789          | `johndoe@example.com` | Marketing  |
| 2          | Jane Smith    | 28   | Female | 234-56-7890          | `janesmith@example.com` | Sales      |
| 3          | Robert Johnson | 45   | Male   | 345-67-8901          | `rjohnson@example.com` | HR         |

In this table, the composite key consists of the combination of the `EmployeeID` and `Department` fields. This means that the combination of these two fields is unique for each row in the table.

## Natural key

| ProductID | ProductName        | ProductCategory | ProductDescription               |
|-----------|--------------------|-----------------|---------------------------------|
| 1         | Chocolate Cake     | Dessert         | Delicious chocolate cake with... |
| 2         | Blueberry Muffins  | Bakery          | Freshly baked blueberry muffins |
| 3         | Grilled Cheese Sandwiches | Lunch      | Delicious grilled cheese sand... |

In this table, the natural key is the `ProductID` field. This field is a unique identifier for each row in the table, and it already exists within the data itself (it is not a synthetic key that has been created by the DBMS).

###### Natural Composite key

| CustomerID | FirstName | LastName | EmailAddress        |
|------------|-----------|----------|---------------------|
| 1          | John      | Doe      | `johndoe@example.com` |
| 2          | Jane      | Smith    | `janesmith@example.com` |
| 3          | Robert    | Johnson  | `rjohnson@example.com` |

In this table, the natural composite key consists of the combination of the `FirstName`, `LastName`, and `EmailAddress` fields. This means that the combination of these three fields is unique for each row in the table, and it already exists within the data itself (it is not a synthetic key that has been created by the DBMS).

## Alternate key

| EmployeeID | Name          | Age | Gender | SocialSecurityNumber | EmailAddress        |
|------------|---------------|-----|--------|----------------------|---------------------|
| 1          | John Doe      | 32   | Male   | 123-45-6789          | `johndoe@example.com` |
| 2          | Jane Smith    | 28   | Female | 234-56-7890          | `janesmith@example.com` |
| 3          | Robert Johnson | 45   | Male   | 345-67-8901          | `rjohnson@example.com` |

This table has six columns: a primary key called `EmployeeID`, a name column, an age column, a gender column, and two alternate keys called `SocialSecurityNumber` and `EmailAddress`. Each row in the table represents a different employee, and the values in each column represent the corresponding attribute for that employee.

## Candidate key

| EmployeeID | Name          | Age | Gender | SocialSecurityNumber | EmailAddress        |
|------------|---------------|-----|--------|----------------------|---------------------|
| 1          | John Doe      | 32   | Male   | 123-45-6789          | `johndoe@example.com` |
| 2          | Jane Smith    | 28   | Female | 234-56-7890          | `janesmith@example.com` |
| 3          | Robert Johnson | 45   | Male   | 345-67-8901          | `rjohnson@example.com` |

In this table, the primary key is the `EmployeeID` field, and the candidate keys are the `SocialSecurityNumber` and `EmailAddress` fields. This means that either of these fields could potentially be used as the primary key, but the `EmployeeID` field has been chosen as the primary key for this table.

## Surrogate key

| OrderID | CustomerID | OrderDate       | OrderTotal |
|---------|------------|----------------|------------|
| 1       | 1          | 2021-01-01      | 100.00     |
| 2       | 2          | 2021-01-03      | 50.00      |
| 3       | 3          | 2021-01-05      | 75.00      |

In this table, the surrogate key is the `OrderID` field. This field is a synthetic key that has been created by the DBMS specifically for the purpose of identifying rows in the table. It is not a field that already exists within the data itself.

## Primary Key

| CustomerID | FirstName | LastName | EmailAddress        | PhoneNumber       |
|------------|-----------|----------|---------------------|------------------|
| 1          | John      | Doe      | `johndoe@example.com` | 555-555-1212     |
| 2          | Jane      | Smith    | `janesmith@example.com` | 555-555-1213    |
| 3          | Robert    | Johnson  | `rjohnson@example.com` | 555-555-1214     |

In this table, the primary key is the `CustomerID` field. This field is a unique identifier for each row in the table and is used to ensure the uniqueness of each row. It cannot contain null values and must be unique for each row.

###### How to choose primary key?

	Student table

| SID | RED_ID      | NAME | BRANCH | EMAIL           |
|-----|-------------|------|--------|-----------------|
| 1   | CS-2019-37  | John | CS     | `john@xyz.com`  |
| 2   | CS-2018-02  | Adam | CS     | `adam1@xyz.com` |
| 3   | IT-2019-01  | Adam | IT     | `adam2@xyz.com` |
| 4   | ECE-2019-07 | Elly | ECE    | `elly@xyz.com`  |

Candidate Keys: 
- SID
- REG_ID
- EMAIL

>[!INFO]
>We can use any one candidate key as Primary Key

>[!NOTE]
>Lets assume that we picked **REG_ID** as Primary key than other [[#Candidate key|candidate]] keys will become [[#Alternate key|aternate]] ones

###### Table can exist without a primary key

Technically, a table can exist without a primary key, but this is generally not recommended. A primary key is a field or set of fields in a table that uniquely identifies each row in the table. It is an important aspect of database design and serves several important functions, including:

1. **Ensuring the uniqueness of each row**: A primary key is used to ensure that each row in a table is unique. This is important because it allows the database management system (DBMS) to easily locate and manipulate specific rows in the table.

3. **Establishing relationships between tables**: A foreign key is a field that refers to the primary key of another table. It is used to establish relationships between tables and to enforce referential integrity.

3. **Enforcing data integrity**: Keys can be used to enforce data integrity by preventing the insertion of duplicate values or null values into the key field.

4. **Improving database performance**: Using keys to uniquely identify rows in a table can improve the performance of database queries, since the DBMS can use the keys to quickly locate the relevant rows.

>[!NOTE]
>Overall, a primary key is an essential element of a well-designed database. While it is technically possible to create a table without a primary key, doing so is generally not recommended and can lead to problems with data integrity and database performance

## Foreign key

	Employee table

| Employee  | DepartmentId |
|-----------|------------|
| John      | 1  |
| Jane      | 2      |
| Bob       | 3         |

	Depertment table

| DepartmentId | DepartmentName |
|--------------|----------------|
| 1            | Marketing      |
| 2            | Sales          |
| 3            | IT             |

In this example, the `DepartmentId` column is a foreign key that refers to the primary key in a separate `Department` table. The purpose of using a foreign key is to establish a relationship between the `Employee` table and the `Department` table. the `DepartmentId` column is the primary key of the `Department` table, and the `DepartmentName` column contains the names of the various departments. The `DepartmentId` column is also used as the foreign key in the `Employee` table to establish the relationship between the two tables.

For example, if we wanted to retrieve all employees in the Marketing department, we could use a `JOIN` statement to join the `Employee` table and the `Department` table using the foreign key. This would allow us to pull in both the employee data and the department data for the Marketing department in a single query.

Foreign keys are an important part of database design because they allow us to create relationships between different tables and ensure the integrity of the data. Without foreign keys, it would be much harder to create complex queries and maintain the consistency of the data in a database.





