
## smb linux enumeration
````
enum4linux -a 10.11.1.227
```

## smb vulnerability scan
```
nmap -v -p 139,445 --script=smb-vuln-ms08-067 --script-args=unsafe=1 10.11.1.201
```

