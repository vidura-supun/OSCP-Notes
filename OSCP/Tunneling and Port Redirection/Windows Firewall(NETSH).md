#windows #portredirect #tunneling #pivoting 

![[Pasted image 20230730211907.png]]


```cmd
netsh interface portproxy add v4tov4 listenport=2222 listenaddress=192.168.50.64 connectport=22 connectaddress=10.4.50.215
```
listenaddress is the machine where we are making the changes.

```cmd
netsh interface portproxy show all
```

Clearing the portforward

```cmd
netsh interface portproxy del v4tov4 listenport=2222 listenaddress=192.168.50.64
```


### Add a FW rule if required

```cmd
netsh advfirewall firewall add rule name="port_forward_ssh_2222" protocol=TCP dir=in localip=192.168.50.64 localport=2222 action=allow
```

clearing the rule

```cmd
netsh advfirewall firewall delete rule name="port_forward_ssh_2222"
```
