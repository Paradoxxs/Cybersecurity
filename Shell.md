# Shell 
#exploitation 

Shell is how a hacker get access to the target machine. There exist two different type of shells.


## Connection

### Bind shell
The target create a listener on a port on the target machine for us to connect to. This allows us to connect from anywhere. 

![Netcat bind shell](https://www.hackingtutorials.org/wp-content/uploads/2016/11/Netcat-bind-shell.jpg)

### Reverse shell
The target connect to us on a port we are listening on.

![netcat-reverse-shell](https://www.hackingtutorials.org/wp-content/uploads/2016/11/Netcat-reverse-shell.jpg)


## Staged vs non-staged payloads

### Staged 
Sends the payload in stages, can be less stable

example : windows/meterpreter/reverse_tcp

### non-staged 
Send the full exploit shellcode at once, It larger in size 

windows/meterpreter_reverse_tcp

