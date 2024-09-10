
1. Run a ferobuster

```bash
feroxbuster -u http://192.168.1.1 -r -o h.feroxbust
```

then a one with file extension

```bash
feroxbuster -u http://192.168.227.147:30455 -r -x php
```
2. Check for Vhosts
```bash
wfuzz -H "Host: FUZZ.devvortex.htb" --hc 404,403,302 -H "User-Agent: PENTEST" -c -z file,"/usr/share/seclists/Discovery/DNS/subdomains-top1million-5000.txt" http://devvortex.htb
```
4. Check all inputs for strange behaviour(SQLi)
5. If the website is overly complicated check for exploits with the title.
6. Check source code for comments (Register, new features)
  - Check Register, new features, posts separately 
7. Check evaluations like 4+4 in the comments and posts