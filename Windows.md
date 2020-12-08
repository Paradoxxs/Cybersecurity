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