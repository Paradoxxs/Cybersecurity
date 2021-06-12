??# Windows 
#windows
Windows has two access modes
	-	Kernel mode, Core OS components, drivers (Ring 0)
	-	User mode, Application code, Drivers  (Ring 3)
	API is used to perform action on the kernel mode 

Non-interactive session 
WIndows comes with three non-interactive sessions, the job of these account is to run windows operations services, processes and scheduled tasks. 

| Account               | Description                                                                                              |
| --------------------- | -------------------------------------------------------------------------------------------------------- |
| Local system account  | NT AUTHORITY\System is the most powerful of all accounts its responsible for handling OS related tasks   |
| Local service account | Know as NT AUTHORITY\LocalService can start services, it have the same privilege as a local user account |
|Network service account|NT AUTHORITY\NetworkService have the same access a domain user and local account and responsible for authenticate to certain network session|

	
## File system

FAT32 (file allocation table)
	
## file directory

| Directory                  | Function                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| -------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Perflogs                   | Can hold Windows performance logs but is empty by default.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| Program Files              | On 32-bit systems, all 16-bit and 32-bit programs are installed here. On 64-bit systems, only 64-bit programs are installed here.                                                                                                                                                                                                                                                                                                                                                                                                                               |
| Program Files (x86)        | 32-bit and 16-bit programs are installed here on 64-bit editions of Windows.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| ProgramData                | This is a hidden folder that contains data that is essential for certain installed programs to run. This data is accessible by the program no matter what user is running it.                                                                                                                                                                                                                                                                                                                                                                                   |
| Users                      | This folder contains user profiles for each user that logs onto the system and contains the two folders Public and Default.                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| Default                    | This is the default user profile template for all created users. Whenever a new user is added to the system, their profile is based on the Default profile.                                                                                                                                                                                                                                                                                                                                                                                                     |
| Public                     | This folder is intended for computer users to share files and is accessible to all users by default. This folder is shared over the network by default but requires a valid network account to access.                                                                                                                                                                                                                                                                                                                                                          |
| AppData                    | Per user application data and settings are stored in a hidden user subfolder (i.e., cliff.moore\\AppData). Each of these folders contains three subfolders. The Roaming folder contains machine-independent data that should follow the user's profile, such as custom dictionaries. The Local folder is specific to the computer itself and is never synchronized across the network. LocalLow is similar to the Local folder, but it has a lower data integrity level. Therefore it can be used, for example, by a web browser set to protected or safe mode. |
| Windows                    | The majority of the files required for the Windows operating system are contained here.                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| System, System32, SysWOW64 | Contains all DLLs required for the core features of Windows and the Windows API. The operating system searches these folders any time a program asks to load a DLL without specifying an absolute path.                                                                                                                                                                                                                                                                                                                                                         |
|WinSxS|The Windows Component Store contains a copy of all Windows components, updates, and service packs.|


## Services

| Service                | Description                                                                                                                                                                                                              |
| ---------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
|smss.exe               | Session Manager SubSystem. Responsible for handling sessions on the system.                                                                                                                                              |
|csrss.exe              | Client Server Runtime Process. The user-mode portion of the Windows subsystem.                                                                                                                                           |
|wininit.exe            | Starts the Wininit file .ini file that lists all of the changes to be made to Windows when the computer is restarted after installing a program.                                                                         |
|logonui.exe            | Used for facilitating user login into a PC                                                                                                                                                                               |
|lsass.exe              | The Local Security Authentication Server verifies the validity of user logons to a PC or server. It generates the process responsible for authenticating users for the Winlogon service.                                 |
|services.exe           | Manages the operation of starting and stopping services.                                                                                                                                                                 |
|winlogon.exe           | Responsible for handling the secure attention sequence, loading a user profile on logon, and locking the computer when a screensaver is running.                                                                         |
|System                 | A background system process that runs the Windows kernel.                                                                                                                                                                |
|svchost.exe with RPCSS | Manages system services that run from dynamic-link libraries (files with the extension .dll) such as "Automatic Updates," "Windows Firewall," and "Plug and Play." Uses the Remote Procedure Call (RPC) Service (RPCSS). |
|svchost.exe with Dcom/PnP|Manages system services that run from dynamic-link libraries (files with the extension .dll) such as "Automatic Updates," "Windows Firewall," and "Plug and Play." Uses the Distributed Component Object Model (DCOM) and Plug and Play (PnP) services.|


## Memory
#memory
^0d4da0

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



### WOW64
Collection of DDL that run within 32 bit process, that emulate the requirements for the 32 bit application. DLL such as WoW64.dll run within the 32 bit process to intercept and translate calls. 32 bit DLL are loaded into the application as needed to support functionality. 

### Process environment block
Structure data in a processes user address space that holds information about the process. This information includes items such as the base address of the loaded module the start of the heap , imported DLLs.

### Windows Shellcode 
#shell
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

### Tools
#### Windows sys tools 
The [SysInternals Tools suite](https://docs.microsoft.com/en-us/sysinternals) is a set of sys tools that can for the most be used without installing typing `\\live.sysinternals.com\tools` into a Windows Explorer window.
	

#### [[OllyDbg]] 
allows one to inspect and modify assembly code for compiled binary. API calls can be monitored and intercepted. 


#### [[Immunity Debugger ]]
is an debugger tool based on OllyDbg, supporting python script . A benefit of using immunity debugger is the easy which debugging symbols can be imported. 

#### PEDump
displays the data structure of portable executable. allowing the user to view all headers iwthin the PE file and the section tables, contents RVA infomration, symbol table, relocation information and etc. 

### Secure boot 
With Unified extensible firmware interface (UEFI) firmware module in the motherboard, it checks the digital signature of all boot-up binaries and the firmware itself and load anti-virus drivers as soon as possible. The intention is to detect malware like bootkits. It does not require a trusted platform module or BitLocker drive. 
	
	
### Bitlocker 
Windows tools for encrypting the whole drive or only the part with data stored on. 
Unlocking of bitlocker devices can happen in multiple ways, with windows 7 an pin was used to unlock the drive, with windows 10 sso is now possible allowing the user to unlock the hard drive and login at the same time. Another option is Configure Network Unlock which will contact [[DHCP]] server to unlock the hard drive. ensuring the device can not leave the cooperation network. 

### Early Launch Anti-Malware
Loads all boot driver and check if they are part of the trusted drivers, if not then they wont be loaded. 
	
### Measured Boot
Windows 10 allows for measured boot, which allows a server to verify the integrity of the boot process 
-	The machine  UEFI firmware, stored hash in the TPM of bootloader and boot driver and everything before the anti malware software. 
-	The machine contact the trusted attestation server  and the server returns with a unique client key. 
-	The machine uses the key to sign the logs 
-	The log get send to the server for evaluation of the machine health. 
	
### Workgroups
Stand-alone computer with local account only. 
	
	
### Active directory 
Windows can use [[AD]] to manage multiple computers and users
	
### Windows server update service [[WSUS]]

### NTFS 
Windows NT file system should be used on every hard drive. 
Advanced security settings is used to create access control rules for folder and files 
	
	
### Registry 
All configuration settings for the computer hardware, OS, applications and users are stored in database called registry. The registry can be modified directly using scripts, command line or regedit GUI tool
	
### Bitlocker 
Is method of disk encryption using AES, and boot-up integrity check with TPM 
	
	
### TPM 
Trusted platform module is a chip built into the motherboard of a computer which can perform on-board random number generation, encryption, hashing and other cryptographic operations. The TPM is also a secure storage location for keys, passwords, hashes and other secrets. 
	

	
### Windows firewall 
Built in free [[Firewall]] enabled by default, and allowed to be managed by group policy. Three different network profiles Domain, Public and private. 

### Windows Internet information server (IIS)
Is a collection of services including HTTP, FTP, SMTP and NNTP. It important to have separate drive volumes for OS and web content, always formatted with NTFS. With the latest encryption enabled. 

### Remote desktop service
Is a graphical remote control of virtual desktops running on WIndows. 
Best practices 
	-	Req Network level Authentication
	-	Smart card
	-	Req strong encryption 
	-	Block access to local drives, clipboard and PnP devices. 
	-	Disable service if not needed.
	-	Req passphrase or short TTL for assistance invitations
	-	Investigate Citrix as a cross-platform alternative. 
		
		
### CMD
#cli
#### WMIC 
Can be used to get or set configuration data for a very wide variety of settings. 
#### Cerutil 	
Certutil is a tool  which can be used to encode and decode data from e.g base64, hex, it was created as a tools to encode and decode ssl certificates. 

#### Clip 
Output of cmd can be send to clipboard for later to be pasted. 
e.g. echo test | clip

#### cmdkey 
cmdkey can be used to displayed any saved password on the machine 
cmdkey /list

#### Curl
Is command-line browser similar to wget, that pulls content from a web server. 

#### net1 
same as net command, crated as a remady to y2k and stuck around ever since. 

#### Tar 
allows for archinves one or more files. 

#### Where 
Same command as in linux. 

#### tasklist
list the current task / process 
-m allows you to list the dll the process has loaded. 


#### regsrv32
Stands for Microsoft register server. it's used to register and unregister object linking and embedding controls like dll files and OCX files. by using the command regsrv32 -s <\file name of the dll to be loaded> will tells windows in load that specific dll file. This can be easily be exploited by having the system load an dll with malware in it. 
	
#### Cheatsheet 
	
		[Cheatshet](https://www.sans.org/security-resources/sec560/windows_command_line_sheet_v1.pdf)
		
### Powershell 
	Is both a scripting language and command shell. 
	

### Scheduling jobs 
	Automation of tasks such as scripts. 
^schedule

### Windows logging 
Windows have split the [[Log]] into different type of logs files. 
Logs types
	-	Application
	-	Security
	-	System
	-	Directory Service (Domain controller)
	-	DNS Server (DNS only)
	-	File Replication Service (Domain controllers)
The built-in windows event collector service is a bit like syslog on Linux, event log data is sent over SSL and it uses the Web service management protocol to either pull data from monitored system or push data from the monitored systems to the collector or both. When a monitored system is off-line, its batched -up events will be forwarded to the collector when accessible again.
	
### Sysmon 
#log
System Monitor (Sysmon) is a Windows system service and device driver that, once installed on a system, remains resident across system reboots to monitor and log system activity to the Windows event log. It provides detailed information about process creations, network connections, and changes to file creation time. By collecting the events it generates using [Windows Event Collection](https://msdn.microsoft.com/library/windows/desktop/bb427443(v=vs.85).aspx) or [SIEM](https://en.wikipedia.org/wiki/security_information_and_event_management) agents and subsequently analyzing them, you can identify malicious or anomalous activity and understand how intruders and malware operate on your network.
^Sysmon
	
### Key windows protocol
#network #services
-	SBM : TCP/139/445
-	RPC	:	TCP/135
-	LDAP :	TCP/389/636/3268/3269
-	Kerberos : TCP/UDP/88
-	DNS : UDP/TCP/53
-	RDP : TCP/3389
-	SQL TCP/UDP/1433/1434
-	Netbios: TCP/UDP/137, UDP/138, TCP/139, TCP/UDP/1512, TCP/42
-	IPSec : UDP/500/4500 for IKE, protocols 50 and 51 for ESP and AH

	
## Sysinternals tools 
Is a set of windows application used by administrators, which can be access from both web and share *live.sysinternals.com\tools* which can be used to get information about the device for privilege escalation. 
	
## WMI 
Subsystem for windows powershell which provides admin with monitoring ability. 

## Security identifier (SID)
![[Pasted image 20210531130309.png]]


| Number| Meaning| Description|
| --- | --- | --- |
| S| SID| Identify string as SID|
| 1| Revision number| To this date never changed|
| 5| Identifier-authority | 48-bit string that identifies the computer or network that created the SID|
| 21| SubAuthority1| This is a variable number that identifies the user's relation or group described by the SID to the authority that created it. It tells us in what order this authority created the user's account. |
| 674899381-4069889467-2080702030 | Subauthority2| Tells us which computer (or domain) created the number|
| 1002| SubAuthority3| The RID that distinguishes one account from another. Tells us whether this user is a normal user, a guest, an administrator, or part of some other group|

	
## Registry 
Is a hierarchical database inside windows. It stores low-level settings, and is split up in computer and user, It can be open by typing regedit inside cmd or run. 




## Local group policy 
Is the similar to domain group policy which allows administrator to set policy for network, computer and users. What is allowed and how the system should react. 



## Security 


### user account control (UAC)
UAC is a security feature to prevents malware from running and manipulating processes that could damage the computer or it contents. 

![[uacarchitecture1.png]]


### [[Applocker]]


### Defender 
Windows Default anti-virus