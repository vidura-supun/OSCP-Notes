#OS #linux  #windows 



## Linux

##### Basic
```bash
sudo find / -name *etc 2>/dev/null
```

##### Types

```bash
-type f
-type d
-type l
```

##### Time

```bash
-amin n ##file was last accessed
-cmin n ##status was changed(+24 =)
```

-2 means with[0]\\in last two minutes
+2 means before last two miniutes

##### Size

```bash
-size 8            # Exactly 8 512-bit blocks 
-size -128c        # Smaller than 128 bytes
-size 1440k        # Exactly 1440KiB
-size +10M         # Larger than 10MiB
-size +2G          # Larger than 2GiB
```

##### Operator
**Inverse and execute the LS command**

```bash
find -not -user root -group sudoers  -name flag.txt -exec ls -l {} \;
```




## WIndows

```powershell
Get-ChildItem -Path C:\ -Include *.kdbx -File -Recurse -ErrorAction SilentlyContinue
```
