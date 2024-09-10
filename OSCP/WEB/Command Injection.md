#webapp 

[[Command Injection Cheatsheat]]
[[Lessons Learned]]

Think how the code will work if it was eval() or popen()

Example:

```php
<?php 
popen('echo "hey"&&"ps"', "w")
?>
```

So you have to inject below

```
"&&"ps
```
#### Usefull Commands

**Linux** - whoami, ls, ping, sleep, nc

**Windows** - whoami, dir, ping, timeout