# Tools - Privilege escalation

1. Winpeas
2. sharup
3. powerup

Userpermissions check - accesschk.exe, But old version only supports --accepteula command line option

#### Techniques
1. Kernel exploits

Tools
Windows exploit suggester
Waston - For recent version of Windows

Precompiled kernel exploits
SecWiki

2. Service Misconfigurations

a. Insecure Service Properties

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

b. Unquoted Service Path
c. Weak Registry Permissions
d. Insecure Service Executables
e. DLL Hijacking


