Simple Network Management Protocol is a commonly weak yet heavily used network management protocol found in many networks. 
Usage
	- Monitoring system statics
	- Remote device management
	- Network notification events 

SNMP Framework have typically four components 
	-	Managed Device:  that allows a remote to read and possibly write SNMP variables
	-	Agent: agent is the SNMP service running on the device
	-	NSM Network management system: Management console that collects and set SNMP data on managed devices.
	-	MIB: Management Information Base is the data set reported by SNMP agent on the device. 
	-	Community string: validate NMS access to agents
	
SNMP ALC
	Many networking vendors provide the ability to limit access to the SNMP agent with the use of an access control list (ACL) 
	ACL that it permits access from a defined source IP. 
	
Many implementation have a history of security failures 
 - Default authentication credentials that can not be changed. 
 - Flaws that can be exploited with malformed SNMP traffic with tools such as snmp-fuzzer
 -  Bypassing SNMP ACL
	 -  The ALC is applied to the IP of SNMP traffic but not to the IP used for the [[TFTP]] server, since SNMP is UDP, we can generate spoofed frames using the permitted IP, and write the configuration file to the attackers TFTP server. 

Both SNMPv1 and SNMPv2c are similar, offering no encryption or integrity protection. 
reoying on shared secret to validate NMS access to the agent. 
SNMPv3 add support in three different models 
	-	NoAuthNoPriv 
	- 	authNoPriv (authentication without encryption)
	-	AuthPriv (Authentication and encryption shared HMAC-MD5 or HMAC-SHA) 
	
[[SNMP attacks]] Allows a hacker to gain access to the MIB and view and manipulate SNMP data