SSH
	Secure shell  is a network protocol for operating network service surely over an unsecured network. Typical used in remote command-line, login and remote command execution. 
	Using the private of a user, the user does not need to provide a password for login 
	- e.g. ssh -i <private key> user@<server-ip> 

Linux	
	Linux machine host the private key ssh  in a hidden folder name .ssh the full path of the private key /home/<user>/.ssh the name of the key is id_rsa 
	Autherized_keys tells if other user is allowed to login on this user without knowing the password or having the private key.  ^134d5d