## smb vulnerability scan
```
nmap -v -p 139,445 --script=smb-vuln-ms08-067 --script-args=unsafe=1 10.11.1.201
```

## smb linux enumeration
```
enum4linux -a 10.11.1.227
```

## nmblookup
```
nmblookup -A 10.10.10.10
```

## Find smb share files
```
smbmap -H <IP/HOST>
```
### If you find any folder with READ or WRITE privilages

## connect to smb share folder
```
smbclient //10.10.10.100/Replication -N
smbclient \\\\10.10.10.10\home
smbclient //home/wwwroot -I 10.10.10.10 -N
```
## smb commands
```
get file.txt
cd
ls
```
