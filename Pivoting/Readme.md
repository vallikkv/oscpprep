# SSH pivoting using meterpreter

https://www.hackingarticles.in/ssh-pivoting-using-meterpreter

# Dynamic Port forwarding command (Need SSH credentials of remote server)
sudo ssh -N -D 127.0.0.1:8080 remoteuser@<IP address>

And proxychains should be installed and configured along with dynamic port forwarding
/etc/proxychains.conf

socks4 127.0.0.1 8080

# Nmap scan
proxychains nmap -sT -v scanme.org
