https://book.hacktricks.xyz/network-services-pentesting/pentesting-imap

1. Try to find usernames and passwords
2. Then either straightaway send the payload or read emails for hints
### POP/IMAP

#### POP
```bash
nc -nv 192.168.220.140 110 
```

```
USER john
```

```
PASS SicMundusCreatusEst
```

```
list
```

```
retr 1
```

#### IMAP

```bash
nc -nv 192.168.220.140 143 
```

```
tag login jonas@localhost SicMundusCreatusEst
```

```
tag LIST "" "*"
```

```
tag STATUS INBOX (MESSAGES)
```

```
tag SELECT INBOX
```

```
tag fetch 1:* BODY[HEADER] BODY[1]
```


