Network admission control 

Utilizing NAC leverage a method of network control, that requires end-users to authentication of system policy before being granted access to the network. 
This can be patched with the current anti-virus signature  or two-factor authentication. 
and only be gain access based on the credentials. 

Methods
	[[MAC Address impersonation ]]
	[[User-Agent impersonation]]
	[[TCP stack fingerprinting]]
	
Tools
	[[cpscam]] to impersonate auth client and by pass NAC
	[[OSfuscate]] to bypass TCP stack fingerprinting
	
Scenario 
	- Simple authentication, ensure client meet minimum policy requirements. 
	Commonly implemented as dissolvable agent or clientless NAC.
	Client connects to initial restricted network, where they have access to web portal for authentication and the browser perform system validation. 
	- Web portal 
		Might use [[SNMP]] to grant access to a second [[VLAN]]
		if the server uses inline management will grant access after successful authentication. the portal uses the machine mac , IP or both to validate all the traffic. 
		