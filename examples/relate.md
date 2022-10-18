---
description: Working with relations (graph edges)
---

# RELATE

#### To return an array of all the users assigned to a specific contact

```sql
SELECT <-assigned_to<-users.name.first as assignees FROM contacts:1AVySZG6waXVJ8oSIMIv;
```

This will return: \``{assignees: ['Nathan']}`\` if only he is assigned to the contact.

#### To return an entire record, INCLUDING all the users assigned to a specific contact

```sql
SELECT *, <-assigned_to<-users.name.first as assignees FROM contacts:1AVySZG6waXVJ8oSIMIv;
```

#### To select the entire user that is assigned to a specific contact

```sql
SELECT * FROM users 
WHERE ->assigned_to->(contacts WHERE id = contacts:1AVySZG6waXVJ8oSIMIv)
```

#### To select all users with a field included with those that the user is assigned to

```sql
SELECT *, ->assigned_to->contacts AS assigned_to FROM users
```
