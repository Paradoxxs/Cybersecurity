Cmd is the command line tools for windows machines. 
Because it build-in in all windows installation the footprint of using CMD is very small.
Could potentiale go undetected by the admin, [[Firewall]] and [[IDS]]
It possible to create complex commands by using for loops and If statement or combining command together using | 
eg. for /L in (1,1,225) do @ping -n 1 {#.#.#.%i} | find "TTL"
These commands can be stored in scripts call bat file these files are used by cmd to run a series of commands, ensuring the process is the same everytime. 

Cmd allows us to explore and get information of the machine, domain, network and firewall. 

Cmd is also a great way to elevate privilege, by either finding password in reg, cred dump or injection a process.   

Once you have the permission you can also change the configuration of the machine, to get better foothold or setup the exploitation of the next target. 
And from here exploit the next target. 

Crediential dumping 
	With cmd you can create a sam dump that can be used with minikatz to extract password hashes. 
	- reg save HKLM\\SAM {output} 

Cheat sheet: 
https://assets.contentstack.io/v3/assets/blt36c2e63521272fdc/blt4e45e00c2973546d/5eb08aae4461f75d77a48fd4/WindowsCommandLineSheetV1.pdf