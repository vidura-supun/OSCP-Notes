#Lessons_Learned

-  When finding out the web root use phpinfo DOCUMENT_ROOT.

🔴 use URL -> encode key characters in while encoding with URL encode
🔴 Sometimes do the same thing two times or with a revert machine

**Wordpress**

- Password cracking "hashcat -a 0 -m 400 $P$BINTaLa8QLMqeXbQtzT2Qfizm2P/nI0 ../rockyou.txt"
- Password will have escape characters $P$BINTaLa8QLMqeXbQtzT2Qfizm2P\\/nI0 remove them.

🔴 Use incognito if the URL added to /etc/hosts doesnt work.

[[FTP]]
If the connection hangs with Entering "Extended Passive Mode"
```ftp
epsv
```

[[SQLi]]

- When testing stuff in BURP find where the error shows up, find a unique string in the source code and use that to quickly find the SQLi results
```html
Unknown column '10' in 'order clause'  <!-- end subscribe section -->
```


[[Command Injection]]

Windows command  concat
- if ; works its powershell
- if & or && works its CMD

[[Directory Traversal]]
- Check for header which data is being sent
> *Content-Type:  application/x-www-form-urlencoded*

- URL encode the commands 
- Use both / and \
- Curl use --path-as-is if not working

[[Linux Tools]]
```bash
sudo -l ### to check permission
```

[[DNS]]

- Use dig for zone transfers
- Try both domain and with subdomain to dump

[[Scripts]]
- Close the file after opening or they will get corrupt
- Use **bash xxx.sh** if ./ doesnt work 

[[BufferOverflow]]
- Run the program in Immunity because it is paused
- Use a general Value like 3000 if cannot be fuzzed
- Always use b'' when checking bad chars because otherwise it will be translated as two bytes in python
- Use a manual search with binary search if MSF doesnt work and remember EIP strings are in reverse

[[Port Scan]]

- Sometimes NC catches more UDP ports than NMAP
- Host discovery, other than ICMP Nmap uses 443 and 80

[[Escalation Methods]]
- C:\\xampp\\mysql\\bin\\my.ini sometimes contains backup passwords
- in a run as prompt passwords have to typed out

[[Cross Compilation]]
- Always get the raw executable while downloading from github

[[1. Linux PrivEsc  Recon]]
- Add -static flag while compiling to GCC if you get GLIBC_2.34 error

[[CHISEL]]

- If Concat injection commands does not work like && try injecting single commands separately

[[AS-REP Roasting]]
- Let's assume that we are conducting an assessment in which we cannot identify any AD users with the account option Do not require Kerberos preauthentication enabled. While enumerating, we notice that we have GenericWrite or GenericAll permissions5 on another AD user account. Using these permissions, we could reset their passwords, but this would lock out the user from accessing the account. We could also leverage these permissions to modify the User Account Control value of the user to not require Kerberos preauthentication.

[[Kerberoasting]]

- If impacket-GetUserSPNs throws the error "KRB_AP_ERR_SKEW(Clock skew too great)," we need to synchronize the time of the Kali machine with the domain controller. We can use ntpdate3 or rdate4 to do so.
- we are performing an assessment and notice that we have GenericWrite or GenericAll permissions7 on another AD user account. As stated before, we could reset the user's password but this may raise suspicion. However, we could also set an SPN for the user,8 kerberoast the account, and crack the password hash in an attack named targeted Kerberoasting.

- When it comes to paths, always try / and \\ both.
- 