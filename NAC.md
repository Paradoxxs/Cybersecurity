Network admission control 

Utilizing NAC leverage a method of network control, that requires end-users to authentication of system policy before being granted access to the network. 
This can be patched with the current anti-virus signature  or two-factor authentication. 
and only be gain access based on the credentials. 

After the initial access the IP and MAC address is used to validate the connection. 

TCP stack fingerprinting
	An method used to identify the OS of client in a NAC environment through TCP stack fingerprinting. by passively monitor the TCP traffic to identify the characteristics that correlate to known platform. 
	Initial OS Masquerading 
		Few NAC OS detection system can watch every packet 
		Therefor client are only evaluated initially at the connection
		e.g on Cisco system the client is also check every 5 min or more. 
	
JavaScript OS Validation	
	Javascript OS validation is an method used by the NAC captive portal to identify the OS, this is done by inserting Javascript code in a HTTP response that queries browser DOM fields. 
	[[User-Agent impersonation]] can be used to bypass this validation. 
	
Port Authentication Entity (PAE)
	Simple authentication method on wired network using password auth to validate against a [[RADIUS]] server. where an switch forward the traffic between them. 
	before the access to the network the client only have access to the RADIUS server. 
	This leave the RADIUS server up for exploitation using fuzzing  

Methods
	[[MAC Address impersonation ]]
	[[User-Agent impersonation]]
	
Exploit Tools
	[[cpscam]] to impersonate auth client and bypass NAC
	[[OSfuscate]] to bypass TCP stack fingerprinting
	[[Scapy]] Packet crafting tool
	eapmd5fuzzies.py  Fuzz the radius server on PAE.
	
Scenario 
	- Simple authentication, ensure client meet minimum policy requirements. 
	Commonly implemented as dissolvable agent or clientless NAC.
	Client connects to initial restricted network, where they have access to web portal for authentication and the browser perform system validation. 
	- Web portal 
		Might use [[SNMP]] to grant access to a second [[VLAN]]
		if the server uses inline management will grant access after successful authentication. the portal uses the machine mac , IP or both to validate all the traffic. 
		