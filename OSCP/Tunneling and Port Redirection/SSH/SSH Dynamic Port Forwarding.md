#tunneling #linux #portredirect 


```bash
ssh -N -D 0.0.0.0:9999 database_admin@10.4.50.215
```

Use Proxychains to proxy the traffic to the target adding the below.

```
socks5 192.168.50.63 9999
```

### NMAP Scan Through proxychains

[[Proxychains]]
