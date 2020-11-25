Security 660 Advanced penetration testing. exploit and ethical hacking 
This course is the next step after [[Sans 560]]

This course contains the advances methods for ethical hacking. 

Accessing the network using [[Network attacks]]
[[Cryptography]] for pen testers 
Many pen testers skip over crypto in their assessments, with some essential skill, the recognize of exploit of weak cryptography

Attacking with [[Network Booting]]
 	-	pre-boot environment protocols
	-	Conditions and limitation on network bookting
	-	Mechanics to deliver malicious OS over the lan
	- 	exposure to virtual infrastructure and iSCSI components
	
Escaping Restricted Environments 
The process of working with [[Restricted environments ]]
	- Common restrictions placed as security defenses 
	- Working around the restrictions
	- Gaining privileged and unrestricted filesystem access. 
	
	
[[Python]] for Pen-testers
Leveraging [[Scapy]]
[[Fuzzing]] introduction and Operation 

[[Reverse engineering ]]

Exploiting [[Linux]] for penetration testers

Exploit [[Windows]] for penetration testing 



*Flashcards*

Which is the default destination address and port for DHCPREQUEST? #flashcard 
IP 255.255.255.255 UDP port 67
---
True or false: BOOTP is routable? #flashcard 
true BOOTP is routable
---
True or false wake on lan is broadcast traffic? #flashcard 
False, wol includes victim MAC
---
True or false PXE via DHCP is the only way to remote boot windows and linux? #flashcard 
False, Most network booting can boot any OS since it is early in the bootstrapping
---

What are the three main categories of restrictions? #flashcard 
Physical, network and internet, windows controls 
---
What three windows tools are we most coneerned wtih executing?  #flashcard 
CMD, notepad and a broswer
---
how can we deliver tools/exploits from our web server despite the target going throug a proxy?  #flashcard 
Local networks are usually exculeded from proxy settings 
---
What two external tools are most helpful when attacking restrocted desktops?  #flashcard 
Metasploit and ikat
---
What function updates the PREV-INUSE flag? #flashcard 
Free()
---

which Linux memory allocator supports threading? #flashcard 
Ptmalloc
---

What is the top-most chunk often called? #flashcard 
The wilderness chuck
---

What system call can you use to restore right? #flashcard 
setreuid()
---

To which register would you load the desired system call number? #flashcard 
EAX register
---

Which of the follwing is the most common way to set EAX to zero? #flashcard 
xor eax, eax
---

If the stack is marked as non-excutable, what yupe of attack would you attempt? #flashcard 
return to libc
---

What type of canary utilizes the HP-UX urandom strong number generator? #flashcard 
Random Canaries
---

True or false? Pax ASLR implemntation can randomize all 32-bits of a functions location in a processes memory space #flashcard 
False
---

Stack smashing protection (SSP) is based on what well known stack protection tool? #flashcard 
Propolice
---

How large is the cookie used by MS visual studio? #flashcard 
32-bit
---

DEP works by marking pages in physical memory as executable or none executable true or false ? #flashcard 
True : DEP sets a bit to mark pages of memory during allocation
---

ASLR was available to use natively on XP SP2, but had oto be enabled True or false #flashcard 
false : ALSR was not available naively
---
LFH assings block of memory starting from the wilderness chunk true or false? #flashcard 
false : the name wilderness chuck is not used on windows. LFH assigns blocks of memtory where they are available
---

What is stored at fs segment register offset FS:[0x30]? #flashcard 
PEB
---

What DLLs are almost always loads as modules for a program? #flashcard 
Kernel32.dll & ntdll.dll
---
Windows support fork()-ing to create a new process true or false? #flashcard 
False 
---
What is the name of the language used by COM to define interfaces?
IDL Interface definition language 


What code reuse instruction are commonly used when overwirting the SEH chain? #flashcard 
Pop/pop/ret
---

What is the name of the visual C++ compiler flag to add security cookies? #flashcard 
/GS
---

What is located at ESP +8 when the SE handler is called? #flashcard 
EstablisherFrame Field
---

What is the most common way to locate kernel32.dll? #flashcard
PEB
---

What function allows you to obtain the RVA of a desired API? #flashcard 
GetProcAddress()
---

True or false LoadLibrayA() is used to load kernel32.dell into memory? #flashcard 
False
---