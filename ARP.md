Address resolution protocol translate IP to MAC address. 


ARP spoofing
ARP spoofing is a technique used to manipulate a switch allowing an attacker to eavesdrop on LAN activity by creating an [[MITM]]

Procedure 
	- Attack enumerates hosts on the network 
	- Sends ARP reply to target indicating it the default gateway
	- Send default gateway an ARP reply telling he is workstation
	- All from from target is sent through the attacker machine to the default gateway
	
