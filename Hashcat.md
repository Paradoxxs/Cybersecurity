# Hashcat
#Cracking #Password
Hashcat is a password cracking tool


## Cheat sheet
[doc](https://hashcat.net/wiki/doku.php?id=hashcat)
![[HashcatCheatSheet.v2018.1b.pdf]]
[hashmodes](https://hashcat.net/wiki/doku.php?id=example_hashes)

## usage
|command|description|
|---|---|
|-m|set the mode|
|-a|attack mode|
|hashcat -m 0 -a 3 hash| bruteforce md5 hash|

generate a possible wordlist using the clue :
e.g. could be using company name as clue 
**hashcat -r /usr/share/hashcat/rules/best64.rule — stdout clue > password.txt**

Cracking *NTLM* password 
```
hashcat -a 0 -m 1000 hash /usr/share/wordlists/rockyou.txt
--snip --
Session..........: hashcat  
Status...........: Cracked  
Hash.Name........: NTLM  
Hash.Target......: hash  
Time.Started.....: Thu Jun 10 12:05:18 2021 (3 secs)  
Time.Estimated...: Thu Jun 10 12:05:21 2021 (0 secs)  
Guess.Base.......: File (/usr/share/wordlists/rockyou.txt)  
Guess.Queue......: 1/1 (100.00%)  
Speed.#1.........:  3993.8 kH/s (0.45ms) @ Accel:1024 Loops:1 Thr:1 Vec:8  
Recovered........: 2/2 (100.00%) Digests  
Progress.........: 10207232/14344385 (71.16%)  
Rejected.........: 0/10207232 (0.00%)  
Restore.Point....: 10199040/14344385 (71.10%)  
Restore.Sub.#1...: Salt:0 Amplifier:0-1 Iteration:0-1  
Candidates.#1....: alsinah -> almendrarayada  
  
Started: Thu Jun 10 12:04:56 2021  
Stopped: Thu Jun 10 12:05:21 2021
hashcat -a 0 -m 1000 hash /usr/share/wordlists/rockyou.txt --show  
31d6cfe0d16ae931b73c59d7e0c089c0:  
ffb43f0de35be4d9917ac0cc8ad57f8d:alqfna22
--


