# John the Ribber,
#Cracking 


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

