
### Best one

```bash
snmp-check 192.168.153.42
```

```bash
snmpwalk -v 1 -c public 192.168.186.149 NET-SNMP-EXTEND-MIB::nsExtendOutputFull
```


```bash
snmpwalk -c public -v1 10.11.1.14 1.3.6.1.4.1.77.1.2.25 ##enumerating users
```

##### List all and decode 

```bash
snmpwalk -c public -Oa -v1 -t 10 192.168.203.151 
```


#### Check for SNMP Ports

```bash
sudo nmap -sU --open -p 161 192.168.50.1-254 -oG open-snmp.txt
```

#### onesixtyone My Kali

```bash
cd /home/kali/scripts/onesixtyone
```

```bash
onesixtyone -c community -i ips
```



#### Onesixtyone New

```bash
echo public > community
```

```bash
echo private >> community
```

```bash
echo manager >> community
```

```bash
for ip in $(seq 1 254); do echo 192.168.203.$ip; done > ips
```

```bash
onesixtyone -c community -i ips
```


### Windows Strings

1.3.6.1.2.1.25.1.6.0	System Processes
1.3.6.1.2.1.25.4.2.1.2	Running Programs
1.3.6.1.2.1.25.4.2.1.4	Processes Path
1.3.6.1.2.1.25.2.3.1.4	Storage Units
1.3.6.1.2.1.25.6.3.1.2	Software Name
1.3.6.1.4.1.77.1.2.25	User Accounts
1.3.6.1.2.1.6.13.1.3	TCP Local Ports


#### List of MIB and OIDs

https://cric.grenoble.cnrs.fr/Administrateurs/Outils/MIBS/?oid=1.3.6.1.2.1.25