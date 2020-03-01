
## URL enumerate
```
gobuster -u http://<IP>/ -w /usr/share/seclists/Discovery/Web-Content/common.txt -s '200,204,301,302,307,403,500' -e
```
## Wordlists paths
```
DirB - /usr/share/dirb/wordlists/
wfuzz - /usr/share/wfuzz/wordlist/
SecList - /usr/share/seclists/
```
## Poke arround php myadmin
```
url: http://<IP>/phpmyadmin
default credentials:
admin \ "" (blank), admin \ admin, admin \ password
root \ "" (blank), root \ root, root \ password
```
