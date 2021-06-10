# Network
#network

Network models describing the communication. 
![[Pasted image 20210602132631.png]]
Network is segmented into difference layers, the [[OSI]] model describes this, another model is the [[TCP-IP]] These model works in a top to bottom way, adding headers as they go down in layers. 

Network relies on [[IP]] to handle transmission 

Difference type of networks 
	[[LAN]]
	[[WAN]]
	[[MAN]]
	[[Internet]]
	[[PAN]]
	[[VPN]]

Physical topology describe how the network is wired together 
Logical topology describe the rules for sending packets to each other. 

[[Ethernet]]

Collisions to a minimum, systems are required to check wether anyone else is already transmitting before placing a frame on the wire. if another system singal is already on the wire, the system is excepted to wait. 

[[Token ring and FDDI]]

Asynchronous Transfer mode (ATM) before communication can be initiated an virtual path identifiers (VPI) needs to be created, this allows for end to end connectivity. It a very specialized protocol and typically used were there very high speed requirements. 
	
 [[Network devices]] is the hardware used to establish connection. 

### Packet transfer 
The packet goes through each later, where the layer action is performed. 
![[Pasted image 20210602132741.png]]

As it goes through the layer a header is added to the packet to help identify it. 
This process is called encapsulation. 
![[Pasted image 20210602133037.png]]

## Network design
Segments 
	-	Public the resource that reside on the internet, from the perspective of company network cannot be trusted 
	-	DMZ is our contributions to the internet in the form of Web, email DNS records. There should be a segment between DMZ and private
	-	Private These are the company internal network, and should not be available from the internet. 
Using [[Defense in depth]] to protect the network. 
Firewall placement need to be located in a place that allows it to ensure that any outbound traffic is legitimate and inbound connections.
	
High-level diagram of work from home setup 
![[Pasted image 20210602125755.png]]

### Point to point topology 
![[Pasted image 20210602131820.png]]

### Bus 
![[Pasted image 20210602131845.png]]

### Star 
![[Pasted image 20210602131900.png]]

### Ring 
![[Pasted image 20210602131913.png]]

### Mesh 
![[Pasted image 20210602131925.png]]

### Tree 
![[Pasted image 20210602131937.png]]

### Hybrid 
![[Pasted image 20210602131955.png]]

### Daisy chain 
![[Pasted image 20210602132008.png]]

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
## Security 

1.  Everything that need to access from the internet like web application should be in a DMZ to separate the web application from the rest of the network. This also allow the administrator to be additional security between the web application and the rest of the network, there by container if a breach should happen. 
    
2.  Workstations should be on their own network, and in a perfect world, each workstation should have a Host-Based Firewall rule preventing it from talking to other workstations. If a Workstation is on the same network as a Server, networking attacks like `spoofing` or `man in the middle` become much more of an issue.
    
3.  The Switch and Router should be on an "Administration Network." This prevents workstations from snooping in on any communication between these devices. I have often performed a Penetration Test and saw `OSPF` (Open Shortest Path First) advertisements. Since the router did not have a `trusted network`, anyone on the internal network could have sent a malicious advertisement and performed a `man in the middle` attack against any network.
    
4.  IP Phones should be on their own network. Security-wise this is to prevent computers from being able to eavesdrop on communication. In addition to security, phones are unique in the sense that latency/lag is significant. Placing them on their own network can allow network administrators to prioritize their traffic to prevent high latency more easily.
    
5.  Printers should be on their own network. This may sound weird, but it is next to impossible to secure a printer. Due to how Windows works, if a printer tells a computer authentication is required during a print job, that computer will attempt an `NTLMv2` authentication, which can lead to passwords being stolen. Additionally, these devices are great for persistence and, in general, have tons of sensitive information sent to them.

## Proxy 
Proxy is a mediator between the computer and the destination. 
### Forward proxy 
Filter out going traffic
![[Pasted image 20210602132146.png]]

### Reverse proxy
Filter in going traffic
![[Pasted image 20210602132230.png]]


## Subnetting 
Is the process of splitting the network into segments ensuring only certain devices can communicate with each other. 
The common for a home network is a /24 network which allow for 256 devices. but for larger organization 256 IP address is not enough or maybe they have split it up to multiple subnet e.g. for phone it could be 1.1.0.0/20 which would allow for 512 devices. 
It should be noted that the first address of subnet is used for network and the last is boardcast. so when calculating address you have to mines with 2. 

Overview of subnet. 

|subnet|host|network|boardcast|mask
|---|---|---|---|---|
10.1.1.0/24 | 14|10.1.1.0|10.1.1.15|255.255.255.240|
|10.1.1.16/24|14|10.1.1.16|10.1.1.31|255.255.255.240|
|10.1.1.32/27|30|10.1.1.32|10.1.1.63|255.255.255.240|
|10.1.2.0/23|510|10.1.2.0|10.1.3.255|255.255.254.0|



Quick note [[IPv4]] address goes from 0 to 255
A little guide to understanding subnetting and how many IP address that is possible. 
[Subnet](https://docs.google.com/spreadsheets/d/1cD8QtzpEmJUPODsO4oKELdkythsLvq6_X89jfnezPtM/edit)