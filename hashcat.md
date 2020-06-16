hashcat -m 500 -a 3 shadow.txt rockyou.txt --force

#To identify the hash mode & types

```
hashcat --example-hashes  //List all types

hashcat --example-hashes |grep -i <hash type>

hashcat --example-hashes |grep -i krb

```
