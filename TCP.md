Transmission control protocol it establishes a virtual connection reference as session. The purpose of the protocol is to provide a reliable connection between two nodes. 

TCP establishing a connection 
 -	 SYN ->
 -	  <- Syn/Ack
 -	  ACK -> 
The connection will then continue sending ACK packing to each other until the connection is closed. 

The connection is closed 
	 -	FIN ->
	 -	<- ACK
	 -	<- FIN
	 -	FIN ->
Service

|Service|Port|
|---|---|
|http|80|
|telnet|23|
|ssh|22|
|https|443|
|ms-term-serv (RPG)|3389|
|micrsoft-ds (SMB)|445|
|netbios-ssn|139|
|ftp|21|
|msrpc|135|
|smtp|25|

	
Header
	- https://en.wikipedia.org/wiki/Transmission_Control_Protocol#TCP_segment_structure