## Enumeration - Ports and its purposes.

https://sushant747.gitbooks.io/total-oscp-guide/list_of_common_ports.html

## Banner grabbing to check on all ports

```
nc -nv <IP> <port Number> 
-C for CLRF
```

```
telnet <IP> <PORT number>
```

#Nmap scan on all ports

```
nmap -sC -sV -p- -oA full 127.0.0.1
nmap -sU -p- -oA udp 127.0.0.1
```

## Go buster command

```
gobuster dir --url http://10.10.10.37 --wordlist /usr/share/wordlists/dirb/common.txt
```
