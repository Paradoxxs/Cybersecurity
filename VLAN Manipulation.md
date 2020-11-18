The method of leaving the current [[VLAN]] on the switch

Dynamic Trunking protocol 
	Is a Cisco protocol allows switch to negotiate the switchport state. 
	An attack can trick the switch into thinking our system it a switch using 802.1Q tricking the port as a trunk and passing all VLAN traffic. 
	On pen-testing using packet capture filter on DTP if revealing the presence of DTP frame will indicate the switch port is vulnerable to DTP VLAN hopping attack	

Tools 
[[Yersina]]