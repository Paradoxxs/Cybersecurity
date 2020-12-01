Access control is managing what user have access too. 
Method of controls
-	Least privilege is giving the least amount of access they need to do their job. 
-	Need to know give only access when they need it and take it away when it is no longer required. 
-	Separation of duties breaking critical tasks access multiple people to limit point of exposure
-	Rotation of duties on regular basis to prevent anyone from being able to cover their tracks and minimize the chance of collusion 

Techniques 
Discretionary access control consist of control manage by user such as password on documents 
Mandatory access control controls set by the system
Role-based access control user are assign roles which describe what they have access to.
Ruleset access control 
List Based access control
Token bases access control 

[[SSO]] method of only having the user sign in once, limiting account sets. 

Password should never be stored in pain-text or [[Cryptography]], [[Hashing]] is the best option as it not reversible, to protect the password even better salting is used an random set of data added to the password before hashing to have it even harder to crack. 

Password attacks 
	-	Dictionary attack
	-	Hybrid attack : between dictionary and brute force
	-	Brute force attack
	-	Rainbow table : precomputation hash for brute forcing
	Tools
		-	 [[John the Ribber]]
		-	[[Cain]]
	Protection 
		-	Enforce strong password policy
		-	[[One-time password]], [[MFA]] or [[Biometrics]]
		-	Accounts locked after N amount of attempts 
		- 	No re-usage of passwords 
