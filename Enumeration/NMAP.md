##  NMAP commands
nmap -Pn -sV --script vuln -oN vulnscan 10.10.10.40

## Full port scan (Fast)
```
nmap -p- -oA full-noscripts 10.10.10.76  --max-retries 0
```
