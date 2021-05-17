# Namp

-  [[Nmap]] is a [[Port Scanner]] tool, used to discovery open ports, services version and OS fingerprinting

Nmap scripting engine allows for [[Vulnerability Scanning]] for the most common Vulnerability  
Scanning of [[IPv6]] is support  but limited to a single address. 
	- OS fingerprinting, NSE scripts, SYN or connect scans and ping scan. 

## Script
--script
`--script==vuln`  activate all script in vuln category
-   `safe`:- Won't affect the target
-   `intrusive`:- Not safe: likely to affect the target  

-   `vuln`:- Scan for vulnerabilities
-   `exploit`:- Attempt to exploit a vulnerability
-   `auth`:- Attempt to bypass authentication for running services (e.g. Log into an FTP server anonymously)
-   `brute`:- Attempt to bruteforce credentials for running services
-   `discovery`:- Attempt to query running services for further information about the network (e.g. query an SNMP server).
## Usage

|switch|description|
|---|---|
|-A|Agressive mode|
|-sV| version|
|-sT| tcp connect scans|
| -sS| TCP SYN scans|
|-sN| TCP null scans|
|-sF| TCP FIN scans|
|-sX| TCP xmas scans|
|-o| operation system|
|-O| Output|
|-oN| normal output|
|-oG| grabable output|
|-v| Verbose|
|-vv| Very verbose|
| --reason| reason |
|-sU| udp |
|-p-| all ports|
|-p ##| scan port|
|-p ##-##| port range|


	
 Nmap cheat sheet: 
  - https://www.stationx.net/nmap-cheat-sheet/

https://nmap.org/nsedoc/