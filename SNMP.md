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
	
Many implementation have a history of security failures 
 - Default authentication credentials that can not be changed. 
 - Flaws that can be exploited with malformed SNMP traffic with tools such as snmp-fuzzer

Both SNMPv1 and SNMPv2c are similar, offering no encryption or integrity protection. 
reoying on shared secret to validate NMS access to the agent. 
SNMPv3 add support in three different models 
	-	NoAuthNoPriv 
	- 	authNoPriv (authentication without encryption)
	-	AuthPriv (Authentication and encryption shared HMAC-MD5 or HMAC-SHA) 
	
[[SNMP attacks]] Allows a hacker to gain access to the MIB and view and manipulate SNMP data