Sulley is a tool which takes protocol and describe it in a syntax language. Sulley will then iterates throught multiple muations of the data, base on the grammar. 

Session agents
 -	netmon: captures and stored libpcap files for each mutation
 -	procmon : monitors the target process for faults, restarting it as needed
 -	vmcontrol : starts, stops and resets the guest OS; can also take,delete and restore snapshots. 