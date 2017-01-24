# sqlite-unity-plugin

This plugin can be used to access sqlite database for unity projects in android and iOS devices. 

Copy paste the Plugins folder in the Assets folder of your project and follow the points below to access your database in c#.

1) Import the correct namespaces.
```
using UnityEngine;
using System.Data;
using Mono.Data.Sqlite;
using System.IO;
```

2) Open your database connection; if the database name (My_Database) does not exist it will be created.
```
string connection = "URI=file:" + Application.persistentDataPath + "/" + "My_Database";
IDbConnection dbcon = new SqliteConnection(connection);
dbcon.Open();
```
3) Finally create a query to access your database.
```
IDbCommand dbcmd;
IDataReader reader;

dbcmd = dbcon.CreateCommand();
string q_createTable = 
  "CREATE TABLE IF NOT EXISTS " + "my_table" + " (" +
  "id" + " INTEGER PRIMARY KEY, " +
  "val" + " INTEGER )";
  
dbcmd.CommandText = q_createTable;
reader = dbcmd.ExecuteReader();
```
