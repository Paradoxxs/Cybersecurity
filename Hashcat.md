# Hashcat
Hashcat is a password cracking tool

https://www.blackhillsinfosec.com/hashcat-4-10-cheat-sheet-v-1-2018-1/


## usage
generate a possible wordlist using the clue :
e.g. could be using company name as clue 
**hashcat -r /usr/share/hashcat/rules/best64.rule — stdout clue > password.txt**