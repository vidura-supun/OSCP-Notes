#cracking #bruteforce 

### SSH Private Key

```bash
ssh2john id_rsa > ssh.hash
```

Rule File
```bash
[List.Rules:sshRules]
c $1 $3 $7 $!
c $1 $3 $7 $@
c $1 $3 $7 $#
```

```bash
sudo sh -c 'cat /home/kali/oscp/ssh.rule >> /etc/john/john.conf'
```

```bash
john --wordlist=ssh.passwords --rules=sshRules ssh.hash
```


### ZIP File Cracking

```bash
zip2john hey.zip > zip.hash
```

```bash
sudo john --wordlist=/usr/share/wordlists/rockyou.txt zip.hash
```
