Serialization anomaly means that the result of successfully committing a group of transactions is inconsistent with all possible orderings of running those transactions one at a time.

> So what does it means ?

Example: There are two rows in the database. One has the value "**white**" and the other "**black**". Transaction 1 updates all white to black, Transaction 2 all black to white.

**Transaction 1**: 
```SQL
UPDATE table SET value = 'black' WHERE value = 'white'
```

**Transaction 2**:
```SQL
UPDATE table SET value = 'white' WHERE value = 'black'
```
