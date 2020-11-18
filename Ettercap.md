Ettercap is an network manipulation and password sniffing tool. 

with supports for multiple interfaces like [[Yersina]]

Ettercap support multiple methods for achieving [[MITM]] once of these is [[ARP]]
While acting as default gateway it will sniff for passwords 
	- Telnet, FTP, POP3, SSH, SMB, HTTP, MySQL, IMAP, VNC, SNMP 
	and other unencrypted packets. 

Ettercap plugins 
	- SMB downgrade 

Filters
	Ettercap include a languages that can be used to build Ettercap filter, that describe the traffic you want, and change it with any content. 
	This feature is mainly for plaintext protocols, but it also include protocols with weak encryption such as SSHv1 and SSL. 
	- Browser caching, 
	Browser will in the GET request include "If-Modified-Since" header
	and the server will response back with HTTP/304 "Not midified" stopping us from intercepting the data, The solution to this is to remove "If-Modified-Since headers by using filers. 
	- PDF Exploit Delivery 
	Allows us to modify PDF files with exploit from metasploit
	- SMB Capture 
	Start [[Metasploit]] SMB capture, then use Ettercap to force IE to retrieve an image from the attack UNC file share while also leveraging the Ettercap smb_down trying to force devices to use legacy protocols. 
	Metasploit will not have captured their hashed their authentication hashes. 
	

Cheat sheet: 
	https://www.sans.org/reading-room/whitepapers/tools/ettercap-primer-1406