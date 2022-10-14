# CRUD operations

#### Add a table

```sql
CREATE TABLE users
```

#### Delete a table

```sql
REMOVE TABLE users
```

_Be careful. If any records in other tables reference records in the table that you delete, those references will no longer work._

### Records

```sql
CREATE users SET name = 'Bob'
```

_This will create a new record with a random id and set an additional 'name' property with a value of 'Bob'. If the 'users' table doesn't exist it will be created automatically._

#### Add a record with a specific id

```sql
CREATE users:abc123 SET name = 'Bill'
```

#### Add a record with a specific id with integers or special characters

```sql
CREATE users:`456` SET name = 'Bart'ql
```

#### Delete a record

```sql
DELETE users:abc123
```

#### Delete a single field from a record

```sql
UPDATE users:abc123 SET fieldName = None
```
