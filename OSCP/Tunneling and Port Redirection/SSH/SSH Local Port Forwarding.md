#tunneling #portredirect 


```bash
ssh -N -L 0.0.0.0:4455:172.16.215.217:445 database_admin@10.4.215.215
```

0.0.0.0:4455 - local listener
172.16.50.217:445 - forwarder from the second machine

```bash
ss -ntplu
```


