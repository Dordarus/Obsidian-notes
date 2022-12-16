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


