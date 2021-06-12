# SSH
Secure shell  is a network protocol running on port **22** for operating network service securely over an unsecured network. Typical used in remote command-line, login and remote command execution. 

Create a bidirectional ssh tunnel between a host and local machine
````bash
ssh -l localport:localhost:forenport hostname
ssh -l 8443:127.0.0.1:8443 marcus@monitor.htb
````


## Linux	
Linux machine host the private key ssh  in a hidden folder name .ssh the full path of the private key /home/<user>/.ssh the name of the key is id_rsa 
	
By adding once public key to Autherized_keys allows user to login with their private key pair. 
	
Using the private key of the user, one does not need to provide a password for login 
- e.g. ssh -i id_rsa user@target ^134d5d
	
	