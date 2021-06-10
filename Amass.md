# Amass
#Recon #Opensource #intel 

Amass Is a [[OWASP]] project used to perform [[OSINT]] to gather information and using active reconnaissance against a target. [
Sourcec](https://github.com/OWASP/Amass/)

## Install 
```
sudo snap install amass
```

## Usage 
It might be important to use the flag *-r* it identify a dns server to use other wise 
*Configuration error: No root domain names were provided* error might appear. 
basic usage :
```
amass enum -r 8.8.8.8 -d bws.dk
```
[user_guide](https://github.com/OWASP/Amass/blob/master/doc/user_guide.md)


