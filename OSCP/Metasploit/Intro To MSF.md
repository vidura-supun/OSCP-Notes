#exploit #postExploitation #frameworks

🔴 shell_reverse_tcp is non staged and shell/reverse_tcp is staged

### Fix to Database Error

```bash
sudo -u postgres psql
```

```bash
ALTER DATABASE msf REFRESH COLLATION VERSION;
```

### Create a Workspace

```bash
workspace -a pen200
```

### NMAP 

```msf
db_nmap -A 192.168.50.202
```

#### Check the findings

```msf
hosts
```

```msf
services
```

### Auxiliary Modules

```msf
show auxiliary
```

```msf
search type:auxiliary smb
```

```msf
use 56
```

After Selecting 

```msf
info
```

```msf
show options
```
After setting the values
```msf
vilns
```


### Multi Handler

```msf
ctrl+z
```

```msf
sessions -i 1
```

```msf
sessions -n chisel -i 1
```

