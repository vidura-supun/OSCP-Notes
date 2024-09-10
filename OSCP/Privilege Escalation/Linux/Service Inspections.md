#linux #priviledgeEscalation 


```bash
watch -n 1 "ps -aux | grep pass"
```

### Packet Capture

```bash
sudo tcpdump -i lo -A | grep "pass"
```
