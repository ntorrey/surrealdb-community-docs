# FETCH

`FETCH` replaces any Record ID at the specified path, with the full contents of that Record ID. If you want to select only parts of that record id, then you can do that with...

```sql
SELECT *, (SELECT name, description FROM $parent.favoriteColor LIMIT 1) AS favoriteColor FROM person;
```
