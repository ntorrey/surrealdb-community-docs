# Searching

### Search in fields that contain text

```sql
SELECT * FROM tags 
    WHERE (string::lowercase(title) CONTAINS string::lowercase(searchText))
        OR (string::lowercase(description) CONTAINS string::lowercase(searchText))
```

### Return a single record

```
RETURN users:abc123.*
```
