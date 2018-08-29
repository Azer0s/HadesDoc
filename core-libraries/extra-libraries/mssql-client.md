# mssql:client

```javascript
with sqlClient from std:sql
with client as mssqlClient from mssql:client

var client = sqlClient(mssqlClient("Server=myServerAddress;Database=myDataBase;User Id=myUsername; Password=myPassword;"))
```



