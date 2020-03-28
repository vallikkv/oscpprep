# File transfer from Kali to Windows using netcat
(Sender) Kali ====> Windows (Receiver) 
``` 
nc.exe -nlvp 443 > C:\binary.exe 
``` 
``` 
nc -w 3 <Windows IP> 443 < binary.exe 
``` 
