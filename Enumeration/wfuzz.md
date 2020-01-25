# Wfuzz command

```
wfuzz -c -z file,/usr/share/wordlists/dirbuster/directory-list-lowercase-2.3-medium.txt --hc 404,403,401 http://192.68.1.1/FUZZ

wfuzz -c -z file,/usr/share/wfuzz/wordlist/general/common.txt --hc 404,403,401 http://192.68.1.1/FUZZ/file.py
```
