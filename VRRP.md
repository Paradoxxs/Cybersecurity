Virtual router redundancy protocol is very similar to [[HSRP]]
- Mac address 00:00:5e:00:01:XX where XX is the VRRP group 
- multicap group 224.0.0.18

unlike HSRP, VRRP does not use UDP as an IP playload using IP protocol 112 and 8-bit priority field to identify the order of the router to take responsibility for the virtural IP address. 
VRRP does not include any authentication or integrity check, leaving all coonection vulnerable 