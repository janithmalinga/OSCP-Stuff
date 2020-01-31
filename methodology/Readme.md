## ENUMERATION

### Find all open ports
```
nmap -sV -Pn -p- -T4 -A <IP>
```
### Password bruteforce using hydra
```
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
