#ssh #tunneling #portredirect #linux 



![[Pasted image 20230730185938.png]]

```bash
socat TCP-LISTEN:2222,fork TCP:10.4.50.215:22
```

```bash
sshuttle -r database_admin@192.168.50.63:2222 10.4.50.0/24 172.16.50.0/24
```

192.168.50.63 is the internal machine