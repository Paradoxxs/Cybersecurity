# Minikatz 
'Minikatz is a #post-exploitation tool 
It's now well known to extract plaintexts passwords, hash, PIN code and kerberos tickets from memory. mimikatz can also perform pass-the-hash, pass-the-ticket or build Golden tickets.

Minikatz can both be done on the target machine or on dump sam files using the [[CMD]] 

usage : 
output all of the clear text passwords stored on this computer.
````bash
mimikatz # sekurlsa::logonpasswords
````