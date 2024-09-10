#smb #recon #enumerations

[[nbtscan]]
[[NMAP]]
[[SMBClient]]

### NULL Sessions

```bash
cme smb 10.10.10.161 -u '' -p '' --shares
```

```bash
cme smb 10.10.10.161 --pass-pol
```

```bash
cme smb 10.10.10.161 --users
```

```bash
cme smb 10.10.10.161 --groups
```

```bash
smbclient -N -U "" -L //10.10.10.161
```

### Anonymous Login

```bash
cme smb 10.10.10.161 -u '' -p '' --shares
```

```bash
smbclient -N -L //10.10.10.178
```

