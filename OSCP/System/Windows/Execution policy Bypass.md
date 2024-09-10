#defenseevasion #powershell 


```powershell
PowerShell.exe -ExecutionPolicy Bypass -File .runme.ps1
```

if you need to use a x86 payload with a doubleclick use below

```bat
@echo off
%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe -ExecutionPolicy Bypass -File "%~dp0Bypass.ps1"
```

