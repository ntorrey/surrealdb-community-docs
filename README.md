# In General

#### Add a table

```sql
CREATE TABLE users
```

#### Delete a table

```sql
REMOVE TABLE users
```

_Be careful. If any records in other tables reference records in the table that you delete, those references will no longer work._

#### Add a record

```sql
CREATE users SET name = 'Bob'
```

_This will create a new record with a random id and set an additional 'name' property with a value of 'Bob'. If the 'users' table doesn't exist it will be created automatically._

#### Delete a record

```sql
DELETE users:abc123
```

#### Delete a single field from a record

```sql
UPDATE users:abc123 SET fieldName = None
```
