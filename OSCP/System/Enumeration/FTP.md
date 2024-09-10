#enumerations #filetransfer 

#### Anonymous Login Allowed

```bash
ftp anonymous:192.168.201.247 14020
```

or 

```bash
ftp 192.168.1.1
```

```bash
user anonymous
```

```bash
hey@abc.com
```

**Turn off Passive**

```bash
passive off
```


**Set the encoding to Binary**

```
binary
```

```bash
put p.exe
```

#### Get all the files

```bash
wget -m ftp://anonymous:password@192.168.1.17:30021
```

or if no directories

```
prompt off
```

```
mget *
```
