IPv6 Address uses 128-bit compared to [[IPv4]] that used 32-bit
IPV6 can be assign manually or through DHCPv6 or ICMPv6.
Leading 0 are optional 
in IPv6 successive 0 can be shorened with ::
example 
	fe80:0000:0000:0000.ccac:0000:08ac:7405
	fe80::ccac:0:8AC:7405


IPv6 protocol adds a new layer of complexity for hackers, and for the management and monitoring of the enterprise. 
IPv6 also create new opportunity as it brings it new flaws that can lead to bypass IPv4 defense systems. 
IPv6 have unknowingly been adopted in many organizations as component of modern operating systems. This lack of understanding of the IPv6 usage in organizations has lead to a lack of monitoring of IPv6 attacks against devices. 
IPv6 support encryption in the protocol, and authentication of endpoints. 


Were the limited IPv4 address make is possible to perform active scans to identify devices. the size of IPv6 address make active scanning impractical. 
There for passive scanning is used 
Using the address ff02::1 is used for contacting all link-local devices. together with the ping command we can contact all local devices on the network and store the response at neighbors. 
[[Nmap]] allows for scanning of IPV6 hosts but is limited to single host at the time. 

Neighbor impersonation MITM Neighbor solicitation (NS) ^MITM
- Node A send NS to all nodes.
- Node B return a NS 
- Attacker return NA with B mac address with override flag 
- Node A sends all traffic for Node B through the attacker. 

Router Advertisement MItM
 - A send RS to anycast routers FF02::2
 - Router return RA with multicast FF02::1
 - Attacker send RA with highest default router preference. 
 - All A traffic is send over to the attacker. 

Remote attacks 
 - Required direct access to IPV6 ISP or tunneled connection 
 
 Many tools only work with IPv4 Addresses, a way to overcome this can be done using a local proxy that redirect IPv4 to IPV6

The design of IPv6 header
![Header](https://docs.oracle.com/cd/E23823_01/html/816-4554/figures/HeaderFormat.png)

Cheat sheet: 
 - https://www.roesen.org/files/ipv6_cheat_sheet.pdf