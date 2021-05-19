# JavaScript Deobfuscation
#JavaScript #Deobfuscation #Base64 #HEX #ROT

[[Javascript]] is part of the response of a [[HTTP]] request, which  can return with a [[HTML]] that is comprised of CSS and [[Javascript]], which it code that is run on the client browser unlike PHP and python, .etc which are run on server-side. one of the reason for obfuscating code would be to make it harder for the function of the code to be copied, but it mostly used with malicious intent to bypass web filter etc. and then have the code executed on the target machines. Simple obfuscation techniques are ## Minifying which reduce the code to a single line or packing

e.g. 
```javascript
eval(function(p,a,c,k,e,d){e=function(c){return c};if(!''.replace(/^/,String)){while(c--){d[c]=k[c]||c}k=[function(e){return d[e]}];e=function(){return'\\w+'};c=1};while(c--){if(k[c]){p=p.replace(new RegExp('\\b'+e(c)+'\\b','g'),k[c])}}return p}('5.4(\'3 2 1 0\');',6,6,'Module|Deobfuscation|JavaScript|HTB|log|console'.split('|'),0,{}))
```

The most common encoding used are [[base64]], [[HEX]] and [[ROT]] also know as Caesar cipher 