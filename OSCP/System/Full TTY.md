#tty #shells #reverseShells #bindshells



#### One liners

```bash
python3 -c 'import pty; pty.spawn("/bin/bash")'
```

If this gives an error try,

```bash
python3 -c 'import pty; pty.spawn("/bin/sh")'
```

https://blog.ropnop.com/upgrading-simple-shells-to-fully-interactive-ttys/
```bash
echo os.system('/bin/bash')
```

```bash
/bin/sh -i
```

```bash
script -qc /bin/bash /dev/null
```

```bash
perl -e 'exec "/bin/sh";'
```

```pearl
exec "/bin/sh";
```

```ruby
exec "/bin/sh"
```

```bash
vi: :!bash
```

```bash
IRB: exec "/bin/sh"
```

```bash
vi: :set shell=/bin/bash:shell
```


#### After One Liner

```bash
export TERM=xterm
```

```bash
Ctrl + z
```

```bash
stty raw -echo ; fg
```

```bash
reset
```

#### SOCAT

[[SOcat]]
