Restricted environments is an host or network were the pen-tester only have limited access, Method of escaping the restriction is using [[Privilege escalation]]

Types of Restricted environments 
	-	chroot/jail
	-	SELinux/APPArmor
	-	Windows softare restriction policies (SRP)
	
Windows restricted desktop
	-	Check local admin rights
	-	physical security controls
			BIOS, boot, drive. 
	-	GPO 
		-	Software restriction policies
			-	Levels : Unrestricted
			-	based on Certificate, Hash, Zone, Path
	- AppLocker
		- Deny/Allow user/group specific
Chroot 
	Designed to fake CWD, by hiding the rest of the filesystem from application, it frequently used as a security feature, Chroot set the root directory to were the process is. Chroot gives a false sense of security. It should only be used to test an installation ensuring it only write into a specific folder. 
	- Not virtualized 
	- Not security control
	- Not jail

BSD jails 
	jail set the root directory of a process similarly to that of chroot, but forked prcesses and anything else remains inside the jail and is also restricted. 
	With jails everything is virtualized and isolated except the kernel 
	*The most secure options of the three*

Solaris Zones and Containers 
	It extends the chroot and jail concept, Solaris zone establishes boundaries and the containers are the pseudo-isolated process. This allows for one physical solaris OS to host other version of itself, or another solaris version. This implementation of containers is the same as fully virtualization such as VMware or docker. 
	
	
GRsecurity and PaX
	Is a project that incorporates protections into Linux kernel by set what execution is allow or disallow from specific paths on the filesystem. 
	PaX will prevent many escalations, PaX enhances address-space layout randomization (ASLR) significantly. 
	
Application restrictions 
	[[SELinux]] and AppArmor both have application hardening features. SELinux restrics resources based on inode number from the filesystem. Major difference between SELinux and AppArmor is that AppArmor is fix on the path. Some considered this a better feature as it allow for clearer configuration and usage. However most enviroments allow link on the filesystem which could circumvent a simple implementation of APPArmor.
	AppLocker is an windows equivalent of APPArmor. 

Shell restrictions 


Virtual machine Environment (VME)
	Virtualization architectures have brought an assumption of security with it. The attack surface has increase because there is more functionality to exploit, such as remote access and infrastructure management. The value is also increased as infrastructure virtualization consolidates all controls. 
	
	
	
	
