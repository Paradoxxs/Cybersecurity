# Network
Network is segmented into difference layers, the [[OSI]] model describes this, another model is the [[TCP-IP]] These model works in a top to bottom way, adding headers as they go down in layers. 

Network relies on [[IP]] to handle transmission 

Difference type of networks 
	[[LAN]]
	[[WAN]]
	[[MAN]]
	[[Internet]]
	[[PAN]]

Physical topology describe how the network is wired together 
Logical topology describe the rules for sending packets to each other. 

[[Ethernet]]

Collisions to a minimum, systems are required to check wether anyone else is already transmitting before placing a frame on the wire. if another system singal is already on the wire, the system is excepted to wait. 

[[Token ring and FDDI]]

Asynchronous Transfer mode (ATM) before communication can be initiated an virtual path identifiers (VPI) needs to be created, this allows for end to end connectivity. It a very specialized protocol and typically used were there very high speed requirements. 
	
 [[Network devices]] is the hardware used to establish connection. 

## Network design
Segments 
	-	Public the resource that reside on the internet, from the perspective of company network cannot be trusted 
	-	DMZ is our contributions to the internet in the form of Web, email DNS records. There should be a segment between DMZ and private
	-	Private These are the company internal network, and should not be available from the internet. 
Using [[Defense in depth]] to protect the network. 
Firewall placement need to be located in a place that allows it to ensure that any outbound traffic is legitimate and inbound connections.
	
### MPLS
Multiprotocol label switching (MPLS)  is data forwarding technology that increases the speed and controls the flow of network traffic. With MPLS, data is directed through a path via labels instead of requiring complex lookup in a routing table at every stop. MPLS network make it possible to tie organization network and phone solution together across multiple locations. 
	
## Network protocol 
	Is the agreement or rules on how computer networks communicate with each other. 
	Layer 4 
		- [[UDP]] and [[TCP]] 
	Layer 3 
		- [[ICMP]] 
		
[[Network sniffer]]


## Ports
Ports are the windows or doors to the machine which allows us to communicate too or from machines. 

[Cheatsheet](https://web.mit.edu/rhel-doc/4/RH-DOCS/rhel-sg-en-4/ch-ports.html)