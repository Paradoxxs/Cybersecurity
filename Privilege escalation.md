# Privilege Escalation
#PrivilegeEscalation #Linux #Windows 
Privilege escalation is the process to access higher priv on either the system or domain. 

## [[Linux]] 
[GTFOBins](https://gtfobins.github.io/)

### Credential access

#### [[Reused password]]

#### Credentials from configuration files
Find command for finding config files the user can read
*find / -name \*.conf -perm -u=r 2>/dev/null*
*find / -name \*.config -perm u=r 2>/dev/null*	

#### Credentials from Log files
Find command for finding log files the user can read
*find / -name \*.log -perm -u=r 2>/dev/null	*


#### Credentials from local database

#### Credentials from bash history
User **.bash_history** file

#### [[SSH]] keys 
Check user **.ssh** for Read or write access. 
Read **Id_rsa** private key to **ssh -i  id_rsa user@target**
Add public key to **Authorized_keys** and login with once own private key. 

#### Sudo access
**sudo -l**

#### Group privileges


### Exploit

#### Service running on localhost

#### Kernel Version
Display kernel version: 
cat /proc/version || uname -a ) 2\>/dev/null
lsb\_release -a 2\>/dev/null

Kernel exploit
cat /proc/version
uname -a
searchsploit "Linux Kernel"

#### Binary File version



### Misconfiguration 

#### Processes 
Anything running with more promission then it should? 
ps aux
ps -ef
top -n 1

#### Cron jobs
Any cron jobs running  that is vulnerable, a script that gets executed we can modify, script being executed by root (wildcard vuln? can modify files that root uses? use symlinks? create specific files in the directory that root uses?
crontab -l
ls -al /etc/cron* /etc/at*
cat /etc/cron* /etc/at* /etc/anacrontab /var/spool/cron/crontabs/root 2>/dev/null | grep -v "^#


##### Writeable Cron Job
crontab -e		Edit cron job 


##### Writeable cron job dependency 
crontab -l		Read cron job 
File, python libray, etc.

##### cron jobs wild card
*rsync -a \*.sh rsync://host.back/src/rbd	 # You can create a file called "-e sh myscript.sh" so the script will execute our script*

#### SUID/SGID files

[GTFOBins](https://gtfobins.github.io/)

find . -perm /4000 2>/dev/null				find files with execution perm
find / -perm -u=s -type f 2>/dev/null		find files with special perm

#### Interesting capabilities on binary 


#### Sensitive files writable
/etc/passwd
/etc/shadow
/etc/sudoers
/etc/configuration files


#### Sensitive file readable
/etc/shadow
/root/.ssh/id_rsa


#### Writable PATH 
If you **have write permissions on any folder inside the** **`PATH`** variable you may be able to hijacking some libraries or binaries:

echo $PATH
Root $PATH writable
Directory in PATH Writable


#### LD_PRELOAD set in /etc/sudoers



## Windows 
[lolbins](https://lolbas-project.github.io/)

### Credential access

#### [[Reused Password]]

#### Credentials from configuration files

#### Credentials from local database

#### Credentials from cmdkey

#### Credentials from registry

#### Credentials from unattned or sysprep files

#### Credentials from Log files

#### User groups



### Misconfiguration 

#### User privileges 
whoami /prem


#### Services 
Services from third party vendors are usually the easiest way to get root or admin privilege. Or use processes that behave like a service. 
To escalate using services identify it environment: environment variables, libraries, config files, input files, how is it started. Scheduled task, Anything surrounding the service can be use full. If the service is already running it must be restarted in some way. 
[[Metasploit]] has post exploitation modules. 
[Hacktricks](https://book.hacktricks.xyz/windows/windows-local-privilege-escalation#services)
**CMD**

**Get All services details:**
wmic service get name,pathname,displayname,startmode 

**Find all service which i not in windows folder:**
wmic service get name,displayname,pathname,startmode |findstr /i "Auto" | findstr /i /v "C:\Windows\"



**PS**
**List all services:**
Get-Service

**Get status on specific service:**
Get-Service servicename

**Get all running services:**
Get-Service | Where\-Object {$\_.Status -eq "Running"}

##### Unquoted service path
**CMD**
**Find all service that is unqouted which i not in windows folder:**
wmic service get name,pathname,displayname,startmode | findstr /i auto | findstr /i /v "C:\\Windows\\\\" | findstr /i /v '""'

##### Change Service Binary location

##### Overwrite service Binary

##### [[DLL Hijacking]]

#### AlwaysInstallElevated set in Registry

#### Scheduled tasks 
**CMD**

**Get scheduled tasks:**
schtasks

**Get detailed view of tasks:**
schtasks /query /fo LIST /v

**PS**

**Get scheduled tasks: **
Get-ScheduledTask

**Get tasks details:**
Get-ScheduledTask | ft TaskName,TaskPath,State


##### Executeable files writeable 

##### Dependency Writeable

#### Sensitive files readable 

##### SAM hive

##### System hive












## WIP
- Going from limited access to higher privileges either on the system or domain. 
		- Race conditions
			 Is when order or timing of an application if thrown off you lead to escalation of privilege. 
		- Kernel attacks
			Exploiting flaws in the operation system. 
		- Program or service 
			Making process execute desired higher privilege actions. 
		- Pilfer anything 


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


