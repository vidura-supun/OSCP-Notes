#ssh #tunneling #portredirect #real 


```bash
ssh -N -R 127.0.0.1:2345:10.4.50.215:5432 kali@192.168.45.236
```

2345 - is the listening port in KALI where we will probe with our requests

EX:

```bash
psql -h 127.0.0.1 -p 2345 -U postgres
```

5432 - is the destination port of the server one hop ahead
