#linux #filetransfer #ssh

🔴 Use -r flag if that is a directory

### Upload file 

```bash
scp ~/my_local_file.txt user@remote_host.com:/some/remote/directory
```

### Downloading Files

```bash
scp -P 2222 user@remote_host.com:/some/remote/directory ~/oscp
```

### Using a Key

```bash
scp -i private_key.pem ~/test.txt root@192.168.1.3:/some/path/test.txt
```


### If  SCP gives an Error

scp: Ensure the remote shell produces no output for non-interactive sessions.

- Use -O to use legacy protocol

```bash
scp -O -i id_rsa /home/kali/Downloads/Sorscerer/mhome/max/.ssh/authorized_keys max@192.168.237.100:/home/max/.ssh/authorized_keys

```