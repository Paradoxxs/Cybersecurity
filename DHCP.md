DHCP is in essence [[BOOTP]] with more options, the same UDP ports, options and features of BOOTP. The benefit for DHCP is IP.
It consists of four phases: Discovery, offer, request and acknowledgment.
Client can see many offer broadcast but can only acknowledge to one of them.
a rouge DHCP server or relay controller can force clients to use a default gateway they control, giving them [[MITM]] on all traffic leaving the network. 
[[PXE]] can be used to extend DHCP with OS

Process
	-	Discovery : Client firmware initate UDP broadcast on port 67.
	-	OFFER : DHCP server respond with broadcast to UDP 68.
	-	request: Client send for the offered address on UDP 67
	- 	Acknowledgment: Server send ACK to client 68