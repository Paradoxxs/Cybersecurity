Intrusion detection system is the process of monitoring activity on host or network. Identifying clues that may indicate an attempted or successful breach. An IDS monitor activity that is known or suspected to be malicious in intent, raising alert to be analyzed. The person who is responsible for handling the alerts in the [[Incident Handling]].
IDS does not provide any protection from attacks, it will only [[Alerts]] to the present of the attacks.

Signature analysis 
	Perform pattern matching, where rules indicate criteria in packets that represent events of interest.
	Most implementations of signature analysis utilize a series of rules, where each rule identifies a particular event of interest. The IDS then compare the data received to the rules. 
	
Anomaly analysis
	Baseline of network must be performed as it required the understanding of what normal traffic looks like. It then allows unexpected conditions to be identified as suspicious. 
	
Application/protocol analysis 
	works by examining entirety of protocols and how they operate. based on the implementation and specifications for protocols. Once the IDS has a complete understanding of the protocol and how it operates, it can use exclusive method of identifying anomalous conditions on the network. 
	
Shallow packet inspection 
	The IDS processes only a portion of the packet for analysis. This method evaluates the contents of limited number of fields within the packet. The advantages of this method is that it very fast and can be performed at near wire-speed with optimized hardware. 
	
Deep packet inspection 
	Performs full analysis of the packet. It traditionally deployed at application level firewall gateway, where it has complete understanding of the protocol, it a much slower scanning of packets compared to shallow inspection. 

There are two major version of IDS [[HIDS]] and [[NIDS]]