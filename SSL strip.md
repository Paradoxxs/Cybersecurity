
SSLstrip is a tool that leverage MITM to manipulate web traffic, instead of using invalid certificates, SSLstrip avoid this by instead removing all reference to [[HTTPS]] 

It send all SSL traffic to the intended server but responds with [[HTTP]] back to the victim. 
SslStrip does not allow eavesdrop on activities that is sent directly to HTTPS without first being redirected from HTTP site, this is done by stripping the 302 or 303 message redirecting to HTTPS.  