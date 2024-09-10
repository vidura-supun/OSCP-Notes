
- Lots of ports were open and nothing was found on SMB enum.
- Port 80 had a WEBDAV server but needed authentication 
-  Dumped the LDAP information and searched for the password and got the password description
- Ran a bloodhound and found that it was using LAPS 
- Alternative way is to Put a shell in the WEBDAV server.
- Sprayed with the new password and found Admin