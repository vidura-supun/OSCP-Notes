### If windows path variable is not set

```cmd
set PATH=%PATH%C:\Windows\System32;C:\Windows\System32\WindowsPowerShell\v1.0;
```
### Find in all file contents (Source Code) for SQLi / Password

```bash
grep -Rnw './' -e 'SELECT'
```

### Check if the code is executing in CMD or Powershell

```cmd
(dir 2>&1 *`|echo CMD);&<# rem #>echo PowerShell
```

### Shells in KALI

```bash
cd /usr/share/webshells
```

###  Merge all windows files into one  so you don't need to read individual

```powershell
type note* > new.txt
```

### Merge all the linux files together

```bash
cat ./* > merged-file
```
### Keep Processes running even after SSH disconnect

```bash
nohup long-running-command &
```

Second Way 

CTRL+Z

```bash
bg
disown -h
```
