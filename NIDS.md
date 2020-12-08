Network-based intrusion detection
	Is a [[IDS]] that sits on the network and scan the packet both inbound and outbound, compared to [[Firewall]] which scan the header, NIDS scans the whole packet to detect if the packet is malicious or not. 
	The downside of NIDS compare to [[HIDS]] is that it cannot protect the user if they are not on the network. e.g. working from home.
	
Advantages of NIDS
	-	It easy to scale as any device connected to the network is protected by the NIDS. 
	-	Insight into traffic on the network, by providing summary reports that documents the amount of bandwidth utilized by protocol and application. 
	
Limitations 
	-	Can only analyze the traffic can goes past the NIDS, giving it a hard time analyzing [[Switch]] traffic. 
	-	Bottleneck on the network, and additional task such as decryption, packet reassembly can lead to deceased performance. 
	