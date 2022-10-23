# FETCH

FETCH is only really necessary when you want to return the entire sub-record. Otherwise, just refer to the subfields directly in the `SELECT` statement.

`FETCH` replaces any Record ID at the specified path, with the full contents of that Record ID. If you want to select only parts of that record id, then you can do that with...

```sql
SELECT *, 
    (SELECT name, description FROM $parent.favoriteColor LIMIT 1) AS favoriteColor 
    FROM person;
```

Notice how you don't even need to use FETCH!
