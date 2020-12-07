Firewall
Firewall takes it name from the firewall that is meant to prevent the spread of fire from one portions of structure to another within a building.

Firewall is a network device that provides fundamental network security, by monitoring incoming and outgoing traffic and determining whether to allow or block it, based on rules. Firewalls can come in software or hardware form, as physical devices they are plugged into network infrastructure. This allow us to create private networks, where only intended communications can come in or out.
An shortcoming of Firewalls is that it as silver bullet. 

Default rule
	Default deny - denied all traffic if not otherwise specified
	Default allow - Allows all traffic if not otherwise specified

Filtering 
	Ingress - Only addresses that does not belong to the protected net or reserved ranges are allowed in.
	Egress - Only addresses that belong to the protected net are allowed out onto the internet.
	
Stateless packet filter 
	Analyses each packet by itself with no context of previous packets. And there for have to make assumptions. 
	Data content passes through unchecked. 
	
No state inspection
	The firewall uses TCP flags to determine the state of the connection. 
	The attacker can bypass this by only sending ACK packets. 

Stateful firewalls 
	Maintains state of traffic flows by focusing on the IP and TCP header .

proxy firewalls 
	Are the slowest in performance and the most inconvenient to manage, but usually provide the best security. The default rule is always deny. 
	The firewall disassemble each packet for examination. 
	

Stateful firewalls 
[Firewall](https://www.wesolveit.co.uk/services/data-security/network-security-management/firewall-unified-threat-management/network-firewalls)