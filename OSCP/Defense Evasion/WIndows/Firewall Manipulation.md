#defenseevasion 

[[Windows Firewall(NETSH)]]

### Powershell Disable Firewall

```powershell
Set-NetFirewallProfile -Profile Domain,Public,Private -Enabled False
```

