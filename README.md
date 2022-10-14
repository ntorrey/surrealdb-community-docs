# General CRUD operations

#### Add a record

```sql
CREATE users SET name = 'tobie'
```

This will create a new record with a random id and set an additional 'name' property  with a value of 'tobie'. If the 'users' table doesn't exist it will be created automatically.

#### Delete a record

```sql
DELETE users:if20f1a342fkasdjr59
```

Deletes the record

#### Add a table

```
CREATE TABLE users
```

#### Delete a table

```sql
REMOVE TABLE users
```
