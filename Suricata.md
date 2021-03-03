Suricata is a [IDS] tool 
Documentation : https://suricata.readthedocs.io/en/suricata-4.1.4/rules/intro.html

Rule format :
<action> <protocol> <source> <source port> <direction> <destination> <destination port> (msg: <message>; sid:<signature id>; rev:<revision>;)

alert http any any <> any any (msg:"HTTP traffic";  sid:10000001; rev: 1;)

	Action : 
-   **Pass** – let the packet through without generating an alert;
-   **Drop** – if matched, the packet will be immediately dropped and logged;
-   **Reject** – similarly to the ‘drop’ action, the packet will be immediately dropped and logged, but both the sender and receiver will receive a reject packet;
-   **Alert** – the packet is allowed through but an alert will be generated.

Protocol :
-   tcp (for tcp-traffic)
-   udp
-   icmp
-   ip (ip stands for ‘all’ or ‘any’)
	
	drop tcp [10.53.83.157] any <> any any (msg:"Blcok port scanner";sid:1111;rev1;)
	drop http any  any <> [10.57.139.131] any (msg:"block http hacker";sid:1001;rev:1;)
	
Port : 
\[80, 81, 82\]		port 80, 81 and 82
\[80: 82\]			Range from 80 till 82
\[1024: \]			From 1024 till the highest port-number
!80						Every port but 80
\[80:100,!99\]	Range from 80 till 100 but 99 excluded
\[1:80,!\[2,4\]\]	Range from 1-80, except ports 2 and 4
any
	
Direction	
<> 		both directions
source -> destination

Reload rules :
	sudo suricatasc -c reload-rules
	
Read fast log : 
	tail -f /var/log/suricata/fast.log