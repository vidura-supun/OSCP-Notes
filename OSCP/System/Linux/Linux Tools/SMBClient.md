#smb #recon #linux 

### Basic Command

```bash
smbclient -p 4455 -L //192.168.217.63/ -U hr_admin --password=Welcome1234
```

### Connect to a share

```bash
smbclient //192.168.216.248/transfer -U steven --password=fireball
```
or  with anonymous browsing

```bash
smbclient //192.168.248.71/backups
```
### Download All Files

1. Connect to the share

```SMB
recurse ON
```

```SMB
prompt OFF
```

```
mget *
```





### If the Share/File has a space

```bash
smbclient //192.168.237.175/password\ audit/ -U 'v.ventz' --password='HotelCalifornia194!'
```


```bash
cd "Active directory"
```

### Big Files Download

```bash
smbclient //192.168.237.175/password\ audit/ -U 'v.ventz' --password='HotelCalifornia194!' --socket-options='TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=131072 SO_SNDBUF=131072'
```

```SMB
timeout 120
```

```SMB
iosize 16384
```





