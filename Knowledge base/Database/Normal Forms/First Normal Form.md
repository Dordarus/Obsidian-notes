## Rules for First Normal Form

- **Single Valued Attributes**: Each column of your table should be single valued which means they should not contain multiple values. We will explain this with help of an example later, let's see the other rules for now.

- **Attribute Domain should not change**: This is more of a "Common Sense" rule. In each column the values stored must be of the same kind or type. __For example__: If you have a column `dob` to save date of births of a set of people, then you cannot or you must not save 'names' of some of them in that column along with 'date of birth' of others in that column. It should hold only 'date of birth' for all the records/rows.

- **Unique name for Attributes/Columns**: This rule expects that each column in a table should have a unique name. This is to avoid confusion at the time of retrieving data or performing any other operation on the stored data. If one or more columns have same name, then the DBMS system will be left confused.

- **Order doesn't matters**: This rule says that the order in which you store the data in your table doesn't matter.

### Problem

Subject contains more than 1 value per row

| roll_no | name | subject |
|:-------:|:----:|:-------:|
| 101     | Akon | OS, CN  |
| 103     | Ckon | Ruby    |
| 102     | Bkon | C, C++  |

### In 1NF

Break the values into atomic values

| roll_no | name | subject |
|:-------:|:----:|:-------:|
| 101     | Akon | OS      |
| 101     | Akon | CN      |
| 103     | Ckon | Ruby    |
| 102     | Bkon | C       |
| 102     | Bkon | C++     |
