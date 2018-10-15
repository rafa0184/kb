##SQL Server User Mapping Error 15023

####Problem
```javascript
User, group, or role 'someuser' already exists in the current database. (Microsoft SQL Server, Error: 15023)```


####Solution
```javascript
USE myDB

EXEC sp_change_users_login 'Auto_Fix', 'myUser'```
