# Wfuzz command

wfuzz -c -z file,/usr/share/wordlists/dirbuster/directory-list-lowercase-2.3-medium.txt --hc 404,403,401 http://10.10.10.168:8080/FUZZ
