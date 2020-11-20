Privilege escalation exploits 
	- Going from limited access to higher privileges either on the system or domain. 
			- Race conditions
				 Is when order or timing of an application if thrown off you lead to escalation of privilege. 
			- Kernel attacks
				Exploiting flaws in the operation system. 
			- Program or service 
				Making process execute desired higher privilege actions. 
			- Pilfer anything 
				
				
Services from third party vendors are usually the easiest way to get root or admin privilege. Or use processes that behave like a service. 
To escalate using services identify it environment: enviroment variables, libraries, config files, input files, how is it started. Scheduled task, Anything surrounding the service can be use full. If the service is already running it must be restarted in some way. 
[[Metasploit]] has post exploitation modules. 


Method of escaping 
	-	Manipulate library loading on windows, Look for DDL needed by a EXE run with high priv. 
	-	Changing process reference
	-	Kernel vulnerabilities
	-	VME attack surface, Attack the hypervisor directly
	-	Breaking into VME 
		-	Management network 
				[[MITM]]
		-	VM Network
				Weak guest
				Pivot to another guest 
				if any VM requires promiscuous mode, vSwitch
		- Network storage
			MITM NFS
			MITM iSCSI
	- Breaking out of VME
	- Linux
		- Check for known kernel vulnerabilities. 
		- use Itrace to provide low level behavioral information. 
		- sudo -l : to check what sudo allows. 
	- Windows
		-	Replace shell explore in reg
		-	Using "dialog boxes" allow access to path and files normally hidden for us
			-	e.g. Open Dialog, Print Dialog, Help, Links 
		- Notepad support url in "Open" 
		- MS paint as FTP tool
		


