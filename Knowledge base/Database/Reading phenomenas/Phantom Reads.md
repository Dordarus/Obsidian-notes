If a transaction reads data and then a concurrent transaction _inserts_ data that would have been read in the original transaction, that’s a phantom read.

Let’s use the same example as a non-repeatable read: if our second user _adds_ content in between our first user’s two reads, the first read will be missing data that appears in the second read (this is actually really similar to a non-repeatable read, which is why the same example works).

To avoid all of this nastiness, most SQL databases follow a set of principles called _[[ACID]]_ that prioritises transactional integrity. But the reason principles works is that databases use _[[Database Isolation and read phenomenas| locks]]_ that prevent data from being read or changed while a transaction is making use of it.

### Code example:

TODO
