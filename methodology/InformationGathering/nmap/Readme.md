
## Follow below steps to conduct initial informtion gathering

### First of all do some quick scan
```
nmap --top-ports 10 --open <IP>
```

### Default scan
```
nmap -sC -sV <IP>
```

### Full port scan 
```
nmap -Pn -p- -sV <IP>
```

### Top 100 udp port scan
```
nmap -sU -T4 -p- <IP>
```
