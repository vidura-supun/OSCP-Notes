
#dns #recon 

##### Using host command

```bash
host -t txt megacorpone.com
```

##### Zone Transfer
#zonetransfer 
```bash
host -t ns megacorpone.com | cut -d " " -f 4 ##get name servers
```

```bash
host -l megacorpone.com ns2.megacorpone.com
```

#### Reverse DNS Enumeration

#reversedns

```bash
 for i in $(seq 1 255); host 192.168.174.$i 192.168.174.149 | grep "domain name"
```
