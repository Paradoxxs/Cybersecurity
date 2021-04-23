Sigma is a generic and open signature format that allows you to describe relevant log events in a straightforward manner. The rule format is very flexible, easy to write and applicable to any type of log file. The main purpose of this project is to provide a structured form in which researchers or analysts can describe their once developed detection methods and make them shareable with others.

Sigma uses yaml files which defines the what and how something is detected, from this yaml file it can be translated into other platform specific languages defended upon the organization platforms. 

usage : 

sigmac -t <target platform> <yaml file>
	
Convert a rule of your choice with `sigmac` like `./sigmac -t splunk -c tools/config/generic/sysmon.yml ./rules/windows/process_creation/win_susp_whoami.yml`
	
Convert a whole rule directory with `python sigmac -t splunk -r ../rules/proxy/`

Currently sigma support these platforms: 
[[Splunk]]
[[ELK]]
[[Elasticsearch]]
[[Logpoint]]
[[Microsoft defender ATP]]
[[Azure sentinel]]
[[SumoLogic]]
[[ArcSight]]
[[QRadar]]
[[Qualys]]
[[RSA NetWitness]]
[[Powershell]]


Rule format 
((Sigma rule)https://github.com/SigmaHQ/sigma/wiki/Specification)