#rdp #linux #tool 

#### Basic Usage 

```bash
xfreerdp /cert-ignore /u:admin /p:lab /v:192.168.141.10 /size:1907x987 /compression -themes -wallpaper /audio-mode:1 /auto-reconnect -glyph-cache
```

#### With a .RDP File

```bash
xfreerdp cpub-Paint-QuickSessionCollection-CmsRdsh.rdp /p:XEwUS^9R2Gwt8O914 /u:kiosk
```

#### PTH

```bash
xfreerdp /u:L.Livingstone /pth:19a3a7550ce8c505c2d46b5e39d6f808 /d:resourced.local /v:192.168.237.175 /auto-reconnect /drive:/home/kali/oscp
```

#### Alt

```bash
rdesktop -u admin -p lab 192.168.150.10
```

#### file share

```bash
rdesktop -u offsec -p lab 192.168.188.61 -r disk:linux=/home/kali/oscp
```

```bash
xfreerdp /cert-ignore /u:jason /p:lab /v:192.168.194.203 /drive:/home/kali/oscp 
```
