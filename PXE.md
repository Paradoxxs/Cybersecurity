Portable Execution Environment contains a series of exchanges to dynamically bootstrap an operation system. it used to provide a bootable image to the client as a [[DHCP]] extension after the IP address have been assign 

Process
	-	Client firmware initate UDP broadcast on port 67.
	-	DHCP server respond with broadcast to UDP 68.
	-	Client select PXE boot type by sending packet to UDP port 4011 to the PXE boot server. 
	-	PXE server send info to the client where to find image.
	-	Client request file with TFTP.
	-	Client receives NBP, saves it to [[RAM]] and execute. 
	As everything is carried over [[UDP]], anything can be spoofed/raced with a malicious answer. 
	
Equipment is often pre-configured and is already exposed or one step away from being attacked. 

Many WMware products all have network booting turned on in the virtual BIOS. 
Integrated Lights-Out Management and similar technology.

Monitoring PXE traffic can be done with [[WireShark]]
Attacking PXE with [[Scapy]], another method is using [[Ettercap]] as a [[MITM]] between client and DHCP server. 

Wake on LAN 
	Can be used to initiate [[Network Booting]], it requires the victim hardware support it and in a sleep state that can be woken up. The attacker need to target the victim specifically via its MAC. Under these conditions can force a PXE boot. 
	The packet that trigger waking has a flexible format. requiring it to be brute forced. If SecureON password is being used, it have be revealed using [[Eavesdropping attacks]] on WOL traffic.
	
	
Attack process with PXE
 -	Create payload
 -	Config server to deliver payload
 -	boot victim 
 -	sniff for pause in TFTP traffic
 -	Reconfigure server to stop attack
 -	If payload fails 
	 -	Customize payload
	 -	Use another payload
An good payload option is Tiny Linux in less than 8 MB compressed into an ISO. 
[[Metasploit]] has a AUX module for PXExploit.

Bypass secure boot?
	- Use an authorized boot image
	
Ultimate PXE payload
 -	Support 32 and 64 bit
 -	supprot virtualized victims
 -	Support hardware
 -	Minimal changes to the victim
	
Other options
 -	[[Kon-Boot]]


Concept: 
-	Malicious hypervisor, just enough of an OS to boot the victim inside of a controlled environment 
