# Hypertext transfer protocol
#web
HTTP is part of the application layer on [[OSI]] layer. it consists for request and response. The Client makes a request to the web services, which will process the request and return with a reposes with the requested data. 

[[URL]] is used to make request to web services with used [[DNS]] to make the request readable by humans. 
HTTP is a set of protocols which dictate how to machine will communicate with each other when transmitting data e.g. html, images, video etc. 
HTTP uses port 80.


## Flow
![HTTP_Flow](https://academy.hackthebox.eu/storage/modules/35/HTTP_Flow.png)

The user make a request for the website, the request first goes to the [[DNS]] service which will translate the domain name into a IP adress, the request will then to the web service where the request can be processed. in this case the user has made a request for */* which will make the web server request the index.html file, [[HTML]] is a markup language which is understood by all browser, which will allow the content to be displayed at the user end. 


## method 

|Method|Description|
|---|---|
|Get|request information from service|
|POST|Post data to the web service in html body|
|PUT|Create new resource on the server|
|Delete|Remove reousrce from serve|
|Options|information about the server|

## Status code
|code|status|
|---|---|
|200|OK|
|201| created ok|
|301|redirect|
|302| temp redirect|
|401| not authorised|
|403| forbidden|
|404| not found|
|500| internal error|
|503| service unavailable|


## Header
Headers provide an additions way of passing information

|Header|Description|
|---|---|
|General|General information about the web serivce.|
|Entity|Describe information about the entity, content length and type|
|Request| Information about the request useragent, cookies and type of content the browser understand|
|Response|Information about the response, server, cookies and authentication|
|Security|Use for HTTPS, what protocol should be used etc.|
