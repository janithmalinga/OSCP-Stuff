
## System enumeration

### enumerate from meterpreter shell
```
sysinfo
```

### get shell
```
shell
```

### get system info from shell
```
systeminfo
```
this shows us installed date, boot time, hot fixes installed or not.

## User enumeration 

### Find out loggedin user and his privilages
```
whoami
whoami /priv
```

### Find all users on the host
```
net users
```

### Find details of specific user
```
net user janith
```

### metersploit local exploit sugester
```
use post/multi/recon/local_exploit_suggester
```
run this script using the session 


## SAM file path
```
C:\Windows\System32\Config
```
