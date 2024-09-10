#webapp #tool #bruteforce 


1. dir
2. dns
3. fuzz
4. s3
5. vhost

### Gobuster common commands (dir)

```bash
gobuster dir -u http://10.10.195.165/ -w /usr/share/seclists/Discovery/Web-Content/raft-small-words.txt
```

```bash
gobuster dir -u http://10.10.195.165/ -w /usr/share/seclists/Discovery/Web-Content/common.txt
```

### Gobuster Vhost

```bash
gobuster vhost -u http://<remote_ip> -w /usr/share/seclists/Discovery/DNS/subdomains-top1million-110000.txt
```
### When every request giving the same code

```bash
gobuster dir -b "301" -u http://192.168.209.52/ 
```

### API Checking

```bash
touch patterns
```

```json
{GOBUSTER}/v1
{GOBUSTER}/v2
```

```bash
gobuster dir -u http://192.168.50.16:5002 -w /usr/share/wordlists/dirb/big.txt -p pattern
```
