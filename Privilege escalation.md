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

Common 
	Manipulate library loading on windows, Look for DDL needed by a EXE run with high privilege. 
	Changing process reference
	Kernel vulnerabilities
	Lookup service for insecure path, and replace executable with exploit. 
	VME attack surface, Attack the hypervisor directly
	Breaking into VME 
	-	Management network 
			[[MITM]]
	-	VM Network
			Weak guest
			Pivot to another guest 
			if any VM requires promiscuous mode, vSwitch
	- Network storage
		MITM NFS
		MITM iSCSI

Linux
	Check for known kernel vulnerabilities. 
	use Itrace to provide low level behavioral information. 
	sudo -l : to check what the user is allowed to run as sudo. 
		
Windows
	Replace shell explore in reg
	Using "dialog boxes" allow access to path and files normally hidden for us
		-	e.g. Open Dialog, Print Dialog, Help, Links 
	Notepad support url in "Open" 
	MS paint as FTP tool
	NSLookup as File transfer 
		 By hiding data into a TXT record on a domain under our control, pile the TXT data into a file. 
	Use debug.exe to recreate EXE or DLL. 
			Takes ASCII and reads into memory. 
	rundll32.exe load malicious dll
	Office macros


