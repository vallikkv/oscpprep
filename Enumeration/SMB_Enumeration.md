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

# Some other commands

```
smbclient -L 192.168.232.125

smbclient '//192.168.232.135/share$'

smbclient -U 'tyler' //10.10.10.97/new-site
```



If SMB user credentials can be obtained, then by using psexec metasploit module, we can get the reverse shell 


## One of the Best HTB machine to learn SMB Enumeration and exploit without Metasploit

https://www.jdksec.com/hack-the-box/active

It uses impacket python tool through which we could enumerate adminstrator kerberos hashes once we get hold one smb login


## If VHD files are found in SMB, best way is to mount and access those files

Command to mount the SMB folder

Reference: https://0xrick.github.io/hack-the-box/bastion/
          https://hackso.me/bastion-htb-walkthrough/

```
sudo mount -t cifs -o username=guest //10.10.10.134/Backups /mnt/bastion/

sudo mount -t cifs -o username=guest <Remote share folder /mnt/<Mount folder in Kali machine>

```

Mount VHD files from the existing mount 

```
guestmount -a '/mnt/bastion/WindowsImageBackup/L4mpje-PC/Backup 2019-02-22 124351/9b9cfbc4-369e-11e9-a17c-806e6f6e6963.vhd' -m /dev/sda1 --ro /mnt/vhd3
```
