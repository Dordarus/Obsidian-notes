Second level of isolation is ___READ_COMMITTED___, which adds a little locking into the equation to avoid dirty reads. In ___READ_COMMITTED___, transactions can only read data once writes have been committed.