If you’ve got two consecutive reads in one transaction with a concurrent update in between, those reads are going to show different results even though they’re part of the same transaction.

An example might be two writers working on a blog. Our first user starts a transaction that reads a post’s title, writes to the post, and then reads that post’s title again. If a second user changes that post’s title in the middle of the first user’s transaction, the first user is going to see different values for the title across the two reads; or in other words, a non-repeatable read.

### Code example:

TODO