Windows has two access modes
	-	Kernel mode, Core OS components, drivers (Ring 0)
	-	User mode, Application code, Drivers  (Ring 3)
	API is used to perform action on the kernel mode 
	
PE/CONFF utilize import address table (IAT) and export address table (EAT) the IAT holds symbols that require resolution upon program runtime and EAT make available functions local to the program or library that may be used by other executable files.

Windows API 
	is the interface used to provide access to system resources. Functions are grouped together into [[DLL]]. And are used for everything involving OS. 

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
	SafeSEH builds a table of trusted execption handlers during compile-time 
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
The pointer stored inside the TIB points that is part of a linked list of execption handlers and astructures. if an execption occures within a program, the windows OS will use a callback function to allow the program the chance to handle the exception. If the program do not handle the xecption the default handler will pick up the exception and terminate the program. 

WOW64
	Collection of DDL that run within 32 bit process, that emulate the requirements for the 32 bit application. DLL such as WoW64.dll run within the 32 bit process to intercept and translate calls. 32 bit DLL are loaded into the application as needed to support functionality. 

Process environment block
	structure data in a processes user address space that holds information about the process. This information includes items such as the base address of the loaded module the start of the heap , imported DLLs.

	
Tools
[[OllyDbg]] allows one to inspect and modify assembly code for compiled binary. API calls can be monitored and intercepted. 


[[Immunity Debugger ]] is an debugger tool based on OllyDbg, supporting python script . A benefit of using immunity debugger is the easy which debugging symbols can be imported. 

PEDump displays the data structure of portable executable. allowing the user to view all headers iwthin the PE file and the section tables, contents RVA infomration, symbol table, relocation information and etc. 

