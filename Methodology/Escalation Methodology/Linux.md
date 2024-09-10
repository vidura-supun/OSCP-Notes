[[1. Linux PrivEsc  Recon]]

1. Start with the below
```bash
sudo -l
```

2. Check for passwords in web directory
```
EX: 

define('DBHOST', '127.0.0.1');
define('DBUSER', 'root');
define('DBPASS', 'MalapropDoffUtilize1337');
define('DBNAME', 'SimplePHPGal');

```
