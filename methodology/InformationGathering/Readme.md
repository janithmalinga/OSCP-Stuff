
## Follow below steps to conduct initial informtion gathering

### First of all do some quick scan
```
nmap --top-ports 10 --open <IP>
```
### Full port scan 
```
nmap -Pn -p- -sV --reason <IP>
```

### Top 100 udp port scan
```
nmap -n -A -sU -T4 --top-ports 100 <IP>
```
