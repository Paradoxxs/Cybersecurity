# volatility
[Volatility](https://www.volatilityfoundation.org/) is a[[memory]] forensics tools allowing a person to analyze a memory dump of a computer. 

## cheat sheet
https://book.hacktricks.xyz/forensics/basic-forensic-methodology/memory-dump-analysis/volatility-examples


```
sudo volatility -f Snapshot6.vmem --profile Win7SP1x64 hashdump --output-file=snapshot6.creds
```



#### Vad tag 
When a executable is normaly loaded  it should have memory protection of  PAGE_EXECUTE_WRITECOPY
#### PAGE_EXECUTE_READWRITE
Is a indication that it code injected, because it does not have the expected memory protection. 

#### PAGE_EXECUTE_WRITECOPY



### Plugins 

### Hashdump
Dumps password hashes
#### shutdowntime
Display computer shutdowntime 
#### modules
Will list all kernel modules

#### driverscan 
it list the drivers 

#### callbacks
winows os allows a driver to register a function which will be called when a peticular event occurs, if you see a callback function to a unknown modules is a give away that something specious is happening, and that the malware is using stealth techniques.  

#### pstree 
allows the analyst to get the parent child relationship between processes. 

#### psscan
Generate a dot file which will display parent child relationship in a visual way by using graph 

#### cmdline
Will display the commandline of the process, it requires the input of process id. 

#### netscan
List the network connection that in the memory 

#### yarascan
will scan for pattern that your give it, can be everything. 
Scanning for MZ allows you to search for executable

#### dllist
List the dll uses by the process. 

#### dlldump
dump the dll from memory it requires pid and offset. 

#### moddump
similar to dlldump but this allows you to dump module. 

#### pslist
list the process in the memory

#### dumpregistry
dump the register files from the memory

#### handlles 

#### malfind
scans suspicious memeory location of process

#### vaddump
It dump the process memory region 

#### Hollowfind
hollowfind detects hollowed process by looking for discrepancy between PEB and VAD, it also list processes similar to the hollowed process and suspicious memory regions

##### Hollow process injection 
An indicator of hollow process injection is the ### discrepancy between PEB and Vad 
and vad tag


#### devicetree
Device created by a driver