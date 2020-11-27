User datagram protocol is a simple transport protocol, the goal of UDP is to be fast. it does this by sacrificing error checking, without any guarantee that the packet will arrive. 
Used in cases were packet loss is acceptable like VOIP or video. 
The only security UDP has is the Checksum, tells if the payload or header have been modified in transit, It trivial for a attacker to recompute the checksum and is there for not consider a security feature. 
Protocol using UDP 
	-	NTP 
	-	BOOTP/DHCP
	-	NFS
	-	SNMP
	-	TFTP