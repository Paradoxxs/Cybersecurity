
# HTML 
Hypertext markup language is standard formatting to facilitate uploading of web document. 


## Structure 
HTML uses tags to structure it code indicating elements and type. 
````html
document
 - html
   -- head
      --- title
   -- body
      --- h1
      --- p
````

```html
<!DOCTYPE html>
<html>
    <head>
        <title>Page Title</title>
    </head>
    <body>
        <h1>A Heading</h1>
        <p>A Paragraph</p>
    </body>
</html>
```


## URL Encoding
HTML only understand [[ASCII]] encoding and there for anything that fallout outside of these character have to use URL encoding for the browser to understand it. 
e.g 
|character|encoding|
|space|%20|

