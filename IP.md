 Internet protocol purpose is to handle transmissions of packets between network end point, Host identify with a unique address. Using the [[OSI]] layer 3
[[IPv4]] header
	-	[4Header](https://en.wikipedia.org/wiki/IPv4#Header)
[[IPv6]] header
	-	[6Header](https://en.wikipedia.org/wiki/IPv6_packet#Fixed_header)
IP version used in the IP header tell which version is used. 
Fragmentation attacks is an attack method using IP header, by fragmenting the exploit over multiple packets. 


- is a unique number that that reference to a computer. 
- IPv4 is a 32-bit limit to 4.294.967.296, because of this limit [[NAT]] is used to allowing more computer on the internet
- IPv6 is a 128-bit where the limit is 3.4 x 10↑34

Network address
	Network addressing all nodes on the same network segment must have the same
	network address, two nodes can only have the same host address if they are on different network segments. 
	Subnet mask defines which portion of the address is the network address and which is the host address. 
	example of subnet mask (255.255.255.0 = N.N.N.H)
	Reserved private network address 
		-	10.0.0.0 -> 10.255.255.255
		-	127.16.0.0 -> 172.31.255.255
		-	192.168.0.0 -> 192.168.255.255
	Broadcast addresses are the x.x.x.0 and x.x.x.255 these are reserved for broadcasting. which is a packet that is processed by every IP stack on the LAN. 
	A computer have minimum two addresses [[MAC]] and IP 
	[[DNS]]