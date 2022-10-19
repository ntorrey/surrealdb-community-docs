---
description: Working with relations (graph edges)
---

# RELATE

```sql
SELECT <-assigned_to<-users.name.first as assignees FROM contacts:1AVySZG6waXVJ8oSIMIv;
```

This will return: \``{assignees: ['Bob']}`\` if only he is assigned to the contact.

#### To return an entire record, INCLUDING all the users assigned to a specific contact

```sql
SELECT *, <-assigned_to<-users.name.first as assignees FROM contacts:1AVySZG6waXVJ8oSIMIv;
```

### Bad way

```sql
SELECT * FROM users 
WHERE ->assigned_to->(contacts WHERE id = contacts:1AVySZG6waXVJ8oSIMIv)
```

### Good way

```sql
SELECT <-assigned_to<-users FROM contacts:abc123;
```

#### To select all users with a field included with those that the user is assigned to

### Bad way

```sql
SELECT *, ->assigned_to->contacts AS assigned_to FROM users
```

### Good way

```sql
SELECT ->assigned_to->contacts FROM users:def456;
```
