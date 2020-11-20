Cryptography is the act of encrypting information, ensuring the wrong people can not read the information if the subjected to [[Eavesdropping attacks]], The information is encrypted using a key/secret either a pre-shared in [[Symmetric encryption]] or with a public/private key set in [[Asymmetric encryption]]

Identifying encrypted data, distinguishing encrypted data from random data can be very difficult as encryption should not follow an predictable patterns. 
Create a histogram of the payload bytes, tools such as [[Pcaphistogram]]

Steam Ciphers 
	Stream ciphers is a fast algorithms for encrypting data, but it suffer from a deployment burden, All stream ciphers create keystream data, which is then XOR with the plaintext to produce ciphertext and when reversed. meaning it must not use a key more than once. 
	-	Encrypt one bit at the time.
	- 	Encrypted length is the same as the plaintext
	-	Examples RC4, A5/1, E0 (Bluetooth)
		IV considerations
			- Length 
			- How is it selected
			- Multiple use of the same key
		Exploits
			- Reuse attack
	
Block Cipher
 -	Encrypt data block at a time
 -	Pads the last block to the same block size
 -	Examples AES, DES, 3DES, Blowfish
 -	Block modes: ECB, CBC, CTR
	
	ECB	
		- Encrypts each block with the same key.
		- Identify repetitious block. 

	CBC 
		- Add randomness to each block
		- improves on ECB by preventing duplicate blocks 
			Exploits
				- CBC bit flipping attacks 
				- Oracle padding attacks
		
	CTR
		- IV can never repeat
		- Encrypt all blocks in parallel


Attacking
It every very uncommon to find flaws in widely used protocol such as TLS, GPG and AES 
