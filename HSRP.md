HSRP 
	Hot Standby Router protocol used by cisco for high-availability routers. by default it used plaintext password (defailt password: cisco )
	Support MD5 authentication using shared secret. 

HSRP MITM
	with HSRP authentication key an attack can become MITM 
	- Attacker send HSRP hello with higher priority
	- The former prime and secondary router get down priorities 
	- attacker change mac address to 00:00:0c:=7:ac:xx with default gateway IP 
	- Attacker becomes MITM