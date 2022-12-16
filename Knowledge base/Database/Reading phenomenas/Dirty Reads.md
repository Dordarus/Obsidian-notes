If a transaction is in the middle of updating some data and hasn’t committed yet, and another transaction is allowed to _read_ that uncommitted data, that’s called a dirty read, and could lead to your app showing incorrect data that got rolled back.

An example of a dirty read could be a transaction that invalidates login tokens when a user changes their password. If as the first transaction loads the token, a second one reads that token before the first invalidates it, you’d have yourself a dirty read.

### Code example: 

TODO