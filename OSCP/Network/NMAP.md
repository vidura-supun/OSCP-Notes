#recon #server #tool #network 

[[1. Enumeration Methodology]]

Faster Scan 

```bash
sudo nmap -p- --min-rate=10000 -v -oA nmap/tryhackme 10.10.195.165
```

#### SYN Scan

```bash
sudo nmap -sS 10.11.1.220
```
	For certain proxy through connections
#### Connect Scan 

```bash
nmap -sT 10.11.1.220
```

##### UDP Scan 

```bash
sudo nmap -sU 10.11.1.115
```

🔴 This will give more complete answer

```bash
sudo nmap -sU -sS 192.168.1.1
```

##### Network Sweep 

```bash
nmap -v -sn -PE 10.11.1.1-254 -oG ping-sweep.txt
```

```bash
grep Up ping-sweep.txt | cut -d " " -f 2 > IP-list.txt
```

```bash
sudo nmap -sC -sV -iL IP-list.txt -p 80   
```


#### Service Enumeration Scripts

```bash
ls -1 /usr/share/nmap/scripts/smb*
```

```bash
ls -1 /usr/share/nmap/scripts/nfs*
```

#### RPC Enumeration

```bash
nmap -sV -p 111 --script=rpcinfo 10.11.1.1-254
```

```bash
nmap -p 111 --script nfs* 10.11.1.72
```

### Vulnerability Scan

```bash
sudo nmap -sV -p 443 --script "vuln" 192.168.50.124
```

**Update Database**

```bash
sudo nmap --script-updatedb
```


### Proxychains

```bash
sudo proxychains nmap -vvv -sT --top-ports=20 -Pn -n 10.4.50.64
```

