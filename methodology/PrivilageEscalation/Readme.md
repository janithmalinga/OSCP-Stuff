# LINUX

## Find OS version
```
cat /etc/*-release
uname -i
lsb_release -a
```
## Logged in user
```
id
whoami
pwd
```
## Other users
```
cat /etc/passwd
grep -vE "nologin|false" /etc/passwd
```
## curently running processes
```
ps aux
netstat -antup
```
## What's installed
```
dpkg -l (Debian based OSs)
rpm -qa (CentOS / openSUSE )
uname -a
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

## use a script to find the answers
```
https://github.com/sleventyeleven/linuxprivchecker/blob/master/linuxprivchecker.py
```

## Writable /etc/passwd file found
```
“root::0:0:root:/root:/bin/bash” > /etc/passwd
```

## Try dirty cow exploit
```
https://github.com/FireFart/dirtycow/blob/master/dirty.c
```
