# Digital Forensics
Digital forensics is a branch of forensics science encompassing the recovery and investigation of material found in digital devices, often in relation to computer crime. So, Forensics is the technical process of recovering or collecting evidence that will be used in an investigation. In regards to Security Operations, this discipline is often associated with monitoring of employees to maintain a high-security posture, aiding with incident response to reveal details of how a compromise occurred and any post-actions (known as DFIR), as well as other tasks which require a ‘deep-dive’ into technical aspects.

## Type of forensics 
-	Computer Forensics – Identifying, collecting, and preserving evidence taken from desktops, laptops, and other computer systems and storage media for the purpose of aiding investigations or legal proceedings.
-	Network Forensics – The monitoring, collection, and analysis of network activities such as visited websites and connected IPs, usually associated with incident response and intrusion detection. ^networkforensics
-	Memory Forensics – The process of recovering evidence from the RAM of a running system (also known as live acquisition or live response).
-	Mobile Forensics – The process of recovering evidence from mobile phones, SIM cards, PDAs, tablets, and other mobile devices.
	
	
## Evidence
#### Computer 
Most of the time, evidence will be files and other data on electronic storage media, such as hard-drives in desktops, laptops, and mobile devices

#### Network
Network devices such as a web proxy or router will also hold information about requested sites online.
 
#### Mobile devices
 The wealth of information on our phones is include, and can be very useful to investigators. Evidence such as call history (incoming/outgoing/number/duration), text messages, contacts, web history, images, videos, apps, GPS location, notes, and much more can be retrieved
		 
		 
Handling evidence using [[Chain of custody]]
	 	
		
### Forensic snapshots 
For mission critical internal servers and serves exposed to the internet, your efforts also should include creating periodic system snapshots. It a collection of data that documents the configuration and running state of the machine at a point in time. Its purpose is to provide a baseline against which later snapshot can be compared in order to detect changes. Presumably, we have a before snapshot, when we assume the machine is working fine and no been compromised , and an after snapshot, taken after problems began or after a suspected compromise or just because it's time for another audit. The before and after snapshots can be compared so that only the differences are listed. This process is useful for troubleshooting, but we mainly wish to use these snapshots to detect intrusions, to know how our adversaries have modified our systems, and provide forensics evidence that might be admissible in court of law.
Contents
	-	File hashes 
	-	User Accounts
	-	Group
	-	Shared folders
	-	Account polices
	-	Processes
	-	Device Drivers
	-	Service settings
	-	Network configuration
	-	Listening Ports 
	-	Environmental variables
	-	Registry
	-	NTFS DACLs
	-	IIS configuration 
Bat script tools for producing snapshot. 
[Snapshot](https://gist.github.com/MSAdministrator/502f13e34b689fc9621e5df05afd8341)	
	
### Forensic Techniques 	
#### Feature extraction 
The goal is feature extraction is to identify unique static metadata from files. 
tools such as [[Strings]] is very useful to get metadata about the file. 
Malware comes in many different formats. 

#### Office file
Malware office files frequently comes in form of visual basic macro or excel 4.0 macro. extracting macros from office files with oledump to do static analyze without having to run the malware. Fequently the marco is obfuscatated to make it hard to understand, using deobfuscation tools can help with this. 


#### Behavior extraction 
Behavior extraction is the method of executing the malware and analyzing how what it behavior it doing inside a sandbox. 


### Forensic procedures 
#### Executable Behavior extraction 
WIth the executable in hand, isolating it in a sandbox and executing it there and analyzing the log files of the system is a quick way to get an understanding of the procedure of the malware and what it does and in what order. 
An good example of this is doc files with embedded macros, taking it to a windows sandbox and executing it there to analyze what it does using [[Windows#^Sysmon]]

#### Network 


## Tools
[[Scdbg]]
