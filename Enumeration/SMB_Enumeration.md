# SMB Enumeration


|  SMB 1 	|  Windows 2000, XP and Windows 2003  	|
|---	    |---	                                  |
| SMB 2  	|  Windows Vista SP1 and Windows 2008 	|
| SMB 2.1 |  Windows 7 and Windows 2008 R2      	|
|  SMB 2 	|   Windows 8 and Windows 2012        	|


#### Scanning NETBIOS information
```
nbtscan -r 192.168.1.1
```
#### Enum4linux scanning
```
enum4linux -a 192.168.1.1

enum4linux -r 192.168.1.1
```
#### NMAP scanning
```
nmap -v -p 139,445 --script=smb-os-discovery 192.168.1.1

nmap -v -p 139,445 --script=smb-check-vulns --script-args=unsafe=1 192.168.1.1
```

#### SMBClient command


```
## SMB login with user credentials
smbclient //10.10.10.178/Users -U TempUser  

# 
smbclient -L 10.10.10.178 -N
```

If SMB user credentials can be obtained, then by using psexec metasploit module, we can get the reverse shell 


## One of the Best HTB machine to learn SMB Enumeration and exploit without Metasploit

https://www.jdksec.com/hack-the-box/active

It uses impacket python tool through which we could enumerate adminstrator kerberos hashes once we get hold one smb login



