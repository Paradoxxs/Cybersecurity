DeepBlueCLI is a powershell module for threat hunting via windows event logs. 

DeepBlue comes with evtx log files, which is log files container a specific exploit or malware which an user can use to better understand Deepblue and how it detect things in log files  
evtx file usage: 
	.\\DeepBlue.ps1 .\\evtx\\new-user-security.evtx

usage: 
Deepblue.ps1 -log <log> 
	[e.g.] DeepBlue.ps1 .log security
	
