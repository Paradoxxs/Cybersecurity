- DNS : Domain name system

When make a dns request the machine will first look at hosts file to see if it allready exists, if not it will then try recursive DNS. 

- The purpose of DNS is to translate human resemble to [[IP]]. 
    - ex. google.com : 8.8.8.8
This can either be done using a Domain name system server or the host file. The domain name is read from right to left. ex. www.google.com first .com is lookup then google.com and last www.google.com
exsample of dns request. 
www.google.com
when making a request it will go 
Request for : com 
then google.com
and last www.google.com



Security 
 -	Keep DNS up to date
 -	Destribute authoritative DNS servers
 -	Limit zone transfers
 -	Limit recursive lookups
 -	Register with reputable registrars 
 -	split DNS

DNS cache poisoning attacks involve returning extra data along with the query result. This extra data constrain invalid information which on vulnerable DNS servers will be written to the DNS cache. This will result in any traffic could be redirected. 

If the DNS is down, the machine will sent out a DNS boardcast messages allowing any machines to response with an IP address. 