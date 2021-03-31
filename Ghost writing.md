Ghost Writing is a way of Obfuscating the binary / assembly code in such a way that the signature no longer exists due to malware code obfuscation and no functionality of the malware is lost .  
The Idea here is to add random Assembly instructions to the disassembly of the executable and maitaining the functionality of the malware at the sametime.
This is also called ghostwriting for antivirus
An common way to do this is using [[Metasploit]] msfvenom to output the malware in raw binary. 
use ruby libery metasm (gem install metasm) to convert the binary to assembly code. 
edit the assembly to scamble the signature (common way is before a point get xor with it self, add some random code to the pointer )
convert the assembly code to executable and you have a scambled malware. 


