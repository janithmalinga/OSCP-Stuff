
## Follow below steps to conduct initial informtion gathering

### First of all do some quick scan
```
nmap --top-ports 10 --open <IP>
```
### Full port scan 
```
nmap -Pn -p- -sV --reason <IP>
```

### Full udp port scan
```
nmap -n -A -sU -T4 <IP>
```
