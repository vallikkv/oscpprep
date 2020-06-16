# Wordpress Scanning command

```
// Enumerate all plugins, themes, config backups, DB exports
wpscan --url http://192.168.232.135 --enumerate ap,at,cb,dbe

// General enumeration which also discloses user informationi (Imp!)
 wpscan --url 10.10.10.37 --enumerate -e
```

# Check password

If have access to the folders via SMB or FTP, check config.php file for password

```
Filename: wp-config.php
```
