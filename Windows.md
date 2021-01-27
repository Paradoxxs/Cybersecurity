Windows has two access modes
	-	Kernel mode, Core OS components, drivers (Ring 0)
	-	User mode, Application code, Drivers  (Ring 3)
	API is used to perform action on the kernel mode 
	
	
Memory
	PE/CONFF utilize import address table (IAT) and export address table (EAT) the IAT holds symbols that require resolution upon program runtime and EAT make available functions local to the program or library that may be used by other executable files.
	Windows API is the interface used to provide access to system resources. Functions are grouped together into [[DLL]]. And are used for everything involving OS. 
	Exploit mitigation controls. 
		Application opt-in control 
			-	ASLR 
			-	DEP (Data Execution Prevention)
		OS controls
			-	ASLR
			-	Hardware DEP
		Compile-Time controls
			- Security cookies (canaries)
			-	application ASLR
			-	SafeSEH
		Controls
			SafeSEH builds a table of trusted exception handlers during compile-time 
			99% of windows DLLs on win 7 is compiled with SafeSEH, the problem comes with third party are not compiled with SafeSEH
			GS security check 
				pushes 32-bit security cookie onto the stack to protect return addresses. 
			Heap cookies 
				8-bit in lenght (256 possibilities)
			Safe unlinking 
				combined with cookies and REB randomization. 
			Low Fragmentation heap 
			 - 32-bit cookie
			ASLR
				- Randomizes the image load address once per boot 
					256 locations possibility 
					64K aligned 
				-	PEB is randomized separately
			EMET 
				Greatly increases the difficulty of exploit a vulnerability 
			Thread information block (TIB) or Thread environment block (TEB)
				They are synonymous, the TIB is structure of data that stores information about the current thread, and every thread has one. 
			Structured exception handling (SEH)
				The pointer stored inside the TIB points that is part of a linked list of exception handlers and structures if an exception occurs within a program, the windows OS will use a callback function to allow the program the chance to handle the exception. If the program do not handle the exception the default handler will pick up the exception and terminate the program. 
				^Memory



WOW64
	Collection of DDL that run within 32 bit process, that emulate the requirements for the 32 bit application. DLL such as WoW64.dll run within the 32 bit process to intercept and translate calls. 32 bit DLL are loaded into the application as needed to support functionality. 

Process environment block
	Structure data in a processes user address space that holds information about the process. This information includes items such as the base address of the loaded module the start of the heap , imported DLLs.

Windows Shellcode 
Is used in the same way as on [[Linux#^Shellcode]] spawning a shell, adding account, command execution and practical anything else. Shell on windows have more optaions as it allow DLL injection and installation control software. Shell code is only good for the processor architecture for which it was written for. One of the biggest challenges of writhing shellcode on windows is determining the location of the desired function within the OS. unlike Linux where system calls and function are static between version. On windows it constantly changing.
Windows does not allow for direct access to opening sockets and network ports through direct system calls. you must go through the API function to archive this. 
Forcing the shellcode to use API to make system calls. 
Type of shellcodes
	-	Bind Shell : listen on a port 
	-	Reverse shell : connect to a specified IP address and port
	-	Execute command
	-	Add User
	-	VNC server injection
	-	DLL injection
Multi-stage shellcode for when there not enough space to fit the shellcode, the first-stage loader get additional shellcode over the connection. 	

Tools
[[OllyDbg]] allows one to inspect and modify assembly code for compiled binary. API calls can be monitored and intercepted. 


[[Immunity Debugger ]] is an debugger tool based on OllyDbg, supporting python script . A benefit of using immunity debugger is the easy which debugging symbols can be imported. 

PEDump displays the data structure of portable executable. allowing the user to view all headers iwthin the PE file and the section tables, contents RVA infomration, symbol table, relocation information and etc. 

Secure boot 
	With Unified extensible firmware interface (UEFI) firmware module in the motherboard, it checks the digital signature of all boot-up binaries and the firmware itself and load anti-virus drivers as soon as possible. The intention is to detect malware like bootkits. It does not require a trusted platform module or BitLocker drive. 
	
	
Bitlocker 
Windows tools for encrypting the whole drive or only the part with data stored on. 
Unlocking of bitlocker devices can happen in multiple ways, with windows 7 an pin was used to unlock the drive, with windows 10 sso is now possible allowing the user to unlock the hard drive and login at the same time. Another option is Configure Network Unlock which will contact [[DHCP]] server to unlock the hard drive. ensuring the device can not leave the cooperation network. 

Early Launch Anti-Malware
	Loads all boot driver and check if they are part of the trusted drivers, if not then they wont be loaded. 
	
Measured Boot
	Windows 10 allows for measured boot, which allows a server to verify the integrity of the boot process 
	-	The machine  UEFI firmware, stored hash in the TPM of bootloader and boot driver and everything before the anti malware software. 
	-	The machine contact the trusted attestation server  and the server returns with a unique client key. 
	-	The machine uses the key to sign the logs 
	-	The log get send to the server for evaluation of the machine health. 
	
Workgroups
	Stand-alone computer with local account only. 
	
	
Active directory 
	Windows can use [[AD]] to manage multiple computers and users
	
Windows server update service [[WSUS]]

NTFS 
	Windows NT file system should be used on every hard drive. 
	Advanced security settings is used to create access control rules for folder and files 
	
	
Registry 
	All configuration settings for the computer hardware, OS, applications and users are stored in database called registry. The registry can be modified directly using scripts, command line or regedit GUI tool
	
Bitlocker 
	Is method of disk encryption using AES, and boot-up integrity check with TPM 
	
	
TPM 
	Trusted platform module is a chip built into the motherboard of a computer which can perform on-board random number generation, encryption, hashing and other cryptographic operations. The TPM is also a secure storage location for keys, passwords, hashes and other secrets. 
	
	
APPLocker
	Allows administrators to define which executables can and cannot be run.
	
Windows firewall 
	Built in free [[Firewall]] enabled by default, and allowed to be managed by group policy. Three different network profiles Domain, Public and private. 
	
Windows Internet information server (IIS)
	Is a collection of services including HTTP, FTP, SMTP and NNTP. It important to have separate drive volumes for OS and web content, always formatted with NTFS. With the latest encryption enabled. 

Remote desktop service
	Is a graphical remote control of virtual desktops running on WIndows. 
	Best practices 
		-	Req Network level Authentication
		-	Smart card
		-	Req strong encryption 
		-	Block access to local drives, clipboard and PnP devices. 
		-	Disable service if not needed.
		-	Req passphrase or short TTL for assistance invitations
		-	Investigate Citrix as a cross-platform alternative. 
		
		
CMD
	Command-line 
	WMIC 
		Can be used to get or set configuration data for a very wide variety of settings. 
		
		Cheatsheet : 
			[Cheatshet](https://www.sans.org/security-resources/sec560/windows_command_line_sheet_v1.pdf)
		
Powershell 
	Is both a scripting language and command shell. 
	

Scheduling jobs 
	Automation of tasks such as scripts. 
^schedule

Windows logging 
Windows have split the [[Log]] into different type of logs files. 
	Logs types
		-	Application
		-	Security
		-	System
		-	Directory Service (Domain controller)
		-	DNS Server (DNS only)
		-	File Replication Service (Domain controllers)
	The built-in windows event collector service is a bit like syslog on Linux, event log data is sent over SSL and it uses the Web service management protocol to either pull data from monitored system or push data from the monitored systems to the collector or both. When a monitored system is off-line, its batched -up events will be forwarded to the collector when accessible again.  
	
Key windows protocol
	-	SBM : TCP/139/445
	-	RPC	:	TCP/135
	-	LDAP :	TCP/389/636/3268/3269
	-	Kerberos : TCP/UDP/88
	-	DNS : UDP/TCP/53
	-	RDP : TCP/3389
	-	SQL TCP/UDP/1433/1434
	-	Netbios: TCP/UDP/137, UDP/138, TCP/139, TCP/UDP/1512, TCP/42
	-	IPSec : UDP/500/4500 for IKE, protocols 50 and 51 for ESP and AH
