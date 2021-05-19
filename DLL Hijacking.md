# DLL Hijacking
#Windows #DLL #Presitance #Vulnability

Dll hijacking is the act of looking at which [[DLL]] the application is loading during it startup, because of the way [[WIndows]] search the directory for files it goes from 

dll not allready in memory or known dll
|Search order|description|
|---|
|Application dir| N/A|
|system32| 32-bit dll files in c:\\windows\\system32|
|system| 16-bit dll in c:\\windows\\system|
|Windows| windows directory c:\\Windows|
|Current directory| N/A|
|%path| defined in system environment| 

because of this order the system will try and look it the application directory and if the user have access to create files in the application directory it leans it open to DLL hijacking. 

It important to note there is a reason for the dll to load these files, and if the desired function can not be found the dll will not be loaded properly and malicous code will not be executed properly. 

One option is to implement a simillar function in the malicous dll and have it execute the desired payload. 

## DLL proxying 
This method will create a link between the original dll and the malicious one. 

Application --> dbghelp.dll 
Application --> dbghelp.dll --> dbghelp_org.dll

The application make a request for a dll files but the system find our crafted one, which will in turn communicate with the original dll by using forwarder, this is achieved by using dll wrapper by redirecting these function to the orginal dll using the forwarder function. 


[Article](https://www.blackarrow.net/leveraging-microsoft-teams-to-persist-and-cover-up-cobalt-strike-traffic/)