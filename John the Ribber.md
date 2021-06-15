# John the Ribber,
#Cracking  #Password 


## tools 
John comes with a host of tools which can be used to help crack password
On parrot tools are located at **/usr/share/john/**
*ssh2john.py* Convert ssh private keys to hash that can be cracked by john. 


## Cheat sheet !
[[jtr-cheat-sheet.pdf]]

|Command|Description|
|---|---|
|john hash| simple mode|
|john hash -w wordlist.txt| use word list to crack|
|john hash --show| show cracked passwords|
|john -w wordlist.txt --stdout=8 --rules:Tryout| Generate password candidates max length of 8|
| john --format| hash format|
|john -wordlist=/usr/share/wordlists/rockyou.txt --format=raw-sha1 hash| cracking sha1 with wordlist|
