#tool #cracking #hashes

NETNTLMv2
```bash
hashcat -a 0 -m 5600 hash.txt /usr/share/wordlists/rockyou.txt -r /usr/share/hashcat/rules/rockyou-30000.rule --force
```

#### How to find -m

```bash
hashcat --help | grep -i "ntlm"
```

#### Rules

🔴 If there is a need to add non printable characters or $ use acsii code

```bash
ls /usr/share/hashcat/rules
```

```bash
head /usr/share/wordlists/rockyou.txt > demo.txt
```

```bash
echo \$1 > demo.rule
```

```bash
hashcat -r demo.rule --stdout demo.txt
```

```bash
hashcat -m 0 crackme.txt /usr/share/wordlists/rockyou.txt -r demo3.rule --force
```



#### KeePass Cracking

```bash
keepass2john Database.kdbx > keepass.hash
```
🔴 remove Database part in the hash

```bash
hashcat --help | grep -i "KeePass"
```

```bash
hashcat -m 13400 keepass.hash /usr/share/wordlists/rockyou.txt -r /usr/share/hashcat/rules/rockyou-30000.rule --force
```
