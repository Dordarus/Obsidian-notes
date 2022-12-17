## Database locking and isolation

A modern web application might need to handle hundreds of thousands of transactions daily, and the biggest ones deal with orders of magnitude more than that. That kind of scale can create a bunch of problems with data integrity, starting with the big 3 as defined by the SQL standard and serialization anomaly.

### Reading phenomenas

-  [[Dirty Reads]]
-  [[Non-Repeatable Reads]]
-  [[Phantom Reads]]
-  [[Serialization anomaly]]

### Database isolation levels

-   [[READ_UNCOMMITTED]]
-   [[READ_COMMITTED]] (**PostgreSQL**, **Oracle, MSSQL** default)
-   [[REPEATABLE_READ]] (**MySQL** default)
-   [[SERIALIZABLE]] (**SQLite** default)

## Isolation levels, read phenomena

| **Read Phenomena** / **Isolation level** | **Dirty reads** | **Non-repeatable reads** | **Phantoms** | **Serialisation anomaly** |
| -- | -- | -- | -- | -- |
| **Serializable** | - | - | - | - |
| **Repeatable Read** | - | - | +* | + |
| **Read Committed** | - | + | + | + |
| **Read Uncommitted** | + | + | + | + |

> - don’t occur
> + may occur

> [!NOTE]
>  Phantoms could occur for Repeatable Read isolation level, but not for `SELECT`s, they protected from non-repeatable read and always returns same results


