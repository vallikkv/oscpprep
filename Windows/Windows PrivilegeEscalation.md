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
Command  

```
.\winpeas quiet servicesinfo
```

b. Unquoted Service Path
c. Weak Registry Permissions
d. Insecure Service Executables
e. DLL Hijacking


