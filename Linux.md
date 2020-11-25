Memory 
	Physical memory 
	processor registers look as hard-coded variables. The fastest for the processor to access. 
	Processor Cache is used by the CPU to quickly access instructions and data from memory  Consists of L caches. The closer you get to L1 the smaller the cache is, but also faster to fetch. 
	
		
 [[RAM]]

Paging is performed when the system runs out of memory. The system will copy pages not recently accessed to the hard disk in a area set up as swap space. There by freeing up resources. 
Paging is the process of allowing indirect memory mapping. Linear addressing is mapped into fixed sized pages, most commonly 4KB, Pages mapped into page tables with up to 1024 entries. 

Object files
When high-level programming language such as C or C++ is compiled into object code. This is the representation of the program in binary machine code format. Object file can consists of multiple components.During runtime multiple segments are mapped in memory the prim segments let us walk through each one of the segments so we may further lay a foundation. 



Stack segment short finite operations with predefined buffer sizes rightfully belong on the stack. 
LIFO (Last in, First out)

cdecl caller paces parameters, the called function from right to left and the caller tears down the stack

stdall, Parameters placed by caller from right to left and the called function is responsible for tearing down the stack

GNU Debugger 
that run on UNIX OS, will attach to a process
Similar tool for windows is called MinGW 

AT%T syntax
Source, then destination, eg. mov $4,%eax would copy value 4 into eax. 
last character in operands tell the size b = byte, w = word, l = long

intel syntax 
Destination, then source

Linkers & Loader
Linker link function name to actual location.
Loader load a program from storage to memory. 

objdump used to disassemble object files. 

readelf, display ELF object file information


Dynamic memory 
Heap performing large memory allocation to hold user data or run rick content will utilize heap. Opening multiple Word documents would find the data on the heap. The heap is designed to border a large unused memory segment to allow it to grow without interfering with other memory segments . 

Once a program is loaded into memory, EIP holds the address for the first instruction in the code segment to start the program, also known as the program entry point. The code segment is often loaded at lower memory addresses than other segments. The data segment stores global and static variables used  by the program. With some implementations you will see other segments loaded that could potentially divide up the types of data in the data segment. The BSS segment stores uninitialized variables that may not be needed by the program, or that will remain uninitialized until they are referenced. 
Following the BSS segment is where the heap segment begins for example a web browser need to load an image on a page. memory must be allocated on the heap at this point in order to store the image in memory. The heap grows from lower memory addressing towards the stack segment. starting at a much higher memory address. 

Shellcode 
It primarily used to spawn a shell. Shellcode is usually written in assembly and then assembled into machine code by tools such as netwide assembler. Nowadays it used to thing under the right of the program being compromised. A common usage of shellcode is to bind a shell listening port on the system, add user, dll injection. 
null bytes must not be part of the shell code, because if function hit a null byte it will be translated to a string terminator, causing the shell code to fail. ^Shellcode


Smashing the stack 
4 byte value before the return pointer. UNIX = canary, win Security cookie. 

Terminator canary
Random Canary
Null Canary 

Linux Address space layout randomization (ASLR) 
The primary objective of ASLR and other compile-time controls is to protect programs from being exploited by attackers. one method is to make eligible pages of memory non-writable or non-executable. 
tool: Idd List dynamic dependencies 
Ret to ESP 
	jmp/call esp
ret to exa
	jmp/call exa
ret to ret
	return repeatedly down the stack
ret to ptr
	registers hold addresses on the stack we can control 
	
	