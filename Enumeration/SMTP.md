
# Reference

https://medium.com/@ranakhalil101/hack-the-box-solidstate-writeup-w-o-metasploit-c43063c9ca8e

# SMTP login and check login

```
root@kali:~# telnet 10.10.10.51 110
Trying 10.10.10.51...
Connected to 10.10.10.51.
Escape character is '^]'.
+OK solidstate POP3 server (JAMES POP3 Server 2.3.2) ready 
USER mailadmin
+OK
PASS password
+OK Welcome mailadmin
LIST  
+OK  0
```

```
LIST \\to check any mails
RETR <num> \\ to open that email
```
