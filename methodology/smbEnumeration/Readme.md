## smb vulnerability scan
```
nmap -v -p 139,445 --script=smb-vuln-ms08-067 --script-args=unsafe=1 10.11.1.201
```

## smb linux enumeration
```
enum4linux -a 10.11.1.227
```

## connect to smb share folder
```
smbclient \\\\10.11.1.22\home
```
## smb commands
```
get file.txt
cd
ls
```
