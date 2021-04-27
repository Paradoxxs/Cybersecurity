Security information and event management are where all the [[Log]] data is centralized into one place to be cross examine.

An example of a [[SIEM]] would be elastic with [[ELK]] with [[Elasticsearch]] as its database engine. Another example of SIEM is [[Splunk]].

[[Agent]] or Agent-less?
	When deploying a SIEM we need to retrieve the log data from the servers and endpoint.
	- Agent sitting on the server sending out the data to the SIEM. The downside of this is that the agent will take up computer resources.
	- The other approach is making the SIEM go into the server and retrieve the log data itself. This raises a security problem, as this would mean the SIEM has access to all servers, [[Firewall]], [[Hybervisors]], leaving us with a global service admin account.
	
Logs generates a large amount of data that could exceed SEIM load capacity. A method of dealing with this workload is using a [[Message broker]]. Allowing the SEIM to take messages once it has the capability to handle them. 

