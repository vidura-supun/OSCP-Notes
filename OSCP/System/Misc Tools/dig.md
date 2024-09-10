#dns #recon 


```bash
dig version.bind CHAOS TXT @DNS
```

```bash
dig victim.com mx @<Local_DNS_IP> 
```


#### Zone Transfer
#zonetransfer 

```bash
dig axfr @<DNS_IP> #Try zone transfer without domain
```

```bash
dig axfr @<DNS_IP> <DOMAIN> #Try zone transfer guessing the domain
```

``` bash
fierce --domain <DOMAIN> --dns-servers <DNS_IP> #Will try toperform a zone transfer against every authoritative name server and if this doesn'twork, will launch a dictionary attack
```



