- Webservice "exhibitor for zookeeper"  was vulnerable
```
https://www.exploit-db.com/exploits/48654
```
- After that noticed gcore is allowed with sudo.
- dumped the process 
/usr/bin/password-store
- Used strings to look and found the password of the root.