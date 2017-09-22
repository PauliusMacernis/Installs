Tested on Windows Server 2012 R2 + WampServer2.0c.exe (php 5.2.6 + mysql 5.0.51b + apache 2.2.8)

### Self-signed SSL certificate on windows###  

#### Install OpenSSL ####  
Open SSL requires the Visual C++ 2008 redistributable Before you can install OpenSSL. The link to download both of these is on this page -> http://slproweb.com/products/Win32OpenSSL.html  

#### Open an Elevated Command Prompt ####  
No matter which Windows you're using, hit the Window's Key on your keyboard, type "CMD", then right click on the Command Prompt and choose "Run as Administrator".  
  
Run the following commands in your prompt. Change "apache2.4.9" to whatever version of Apache you have.  
  
cd C:\wamp\bin\apache\apache2.4.9\bin  
  
openssl genrsa -des3 -out server.key 1024  
(Type in your password, verify it)   
(Windows systems do not support pass phrase so skip "-des3" part to skip pass phrase feature)  
  
openssl genrsa -des3 -out server.key 1024  
  
openssl req -new -x509 -nodes -sha1 -days 365 -key server.key -out server.crt -config C:\wamp\bin\apache\apache2.4.9\conf\openssl.cnf  
(Answer a few questions)  
  
Copy the Key and Certificate  
Navigate to: C:\wamp\bin\apache\apache2.4.9\conf  
Create a folder called "ssl.crt" and another folder called "ssl.key"  
Copy the certificate and the key from: C:\wamp\bin\apache\apache2.4.9\bin  
And paste them respectively into the key and certificate folders you just created.  
  
Edit your configuration files  
Navigate to: C:\wamp\bin\apache\apache2.4.9\conf  
Open httpd.conf in your favorite plaintext editor.  
Uncomment the following lines by removing the pound sign (#) from the begining:  
LoadModule ssl_module modules/mod-ssl.so  
LoadModule socache_shmcb_module modules/mod_socache_shmcb.so  
And  
Include conf/extra/httpd_ssl.conf  
Then move the last one after the block of code that starts with <IfModule ssl_module>  
  
Navigate to: C:\wamp\bin\apache\apache2.4.9\bin  
Open php.ini in your favorite plaintext editor.   
Make sure the following line is uncommented by removing the semicolon (;) from the beginning.   
extension=php_openssl.dll   
  
Navigate to: C:\wamp\bin\apache\apache2.4.9\conf\extra   
Open httpd_ssl.conf in a text editor  
Find the line which says <VirtualHost _default_:443>.   
Right after it, change the line which starts with DocumentRoot to: C:/wamp/www/  
Change the line that begins with ErrorLog to: C:/wamp/bin/apache/apache2.4.9/logs/sslerror_log   
Change the line that begins with TransferLog to: C:/wamp/bin/apache/apache2.4.9/logs/sslaccess_log   
Change the line that begins with SSLCertificateFile to: C:/wamp/bin/apache/apache2.4.9/conf/ssl.crt/server.crt  
Change the line that begins with SSLCertificateKeyFile to: C:/wamp/bin/apache/apache2.4.9/conf/ssl.key/server.key  
Find the block of code that starts with <Directory "C:/ And add the following lines to it:   
  
Options Indexes FollowSymLinks MultiViews  
AllowOverride All  
Order allow,deny  
allow from all  
  
Verify that your syntax is correct  
Run the following in the previous command prompt: httpd -t    
  
If any errors pop up, navigate back to the file in question and check out the line number given in the console.   
  
Restart Apache.   
  
If it does not restart well then check for the apache error logs.  
  
More info:  
http://geneticcoder.blogspot.ca/2015/01/how-to-set-up-self-signed-ssl.html  
https://support.quovadisglobal.com/kb/a90/i-get-error-message-error-init-sslpassphrasedialog-builtin-is-not-supported-on-win32.aspx  
https://justin.kelly.org.au/how-to-create-a-self-sign-ssl-cert-with-no-pa/  
http://how2ssl.com/articles/openssl_commands_and_tips/  
http://www.discretelogix.com/blog/miscellaneous/installing-self-signed-ssl-certificate-on-wamp-server  
https://letsencrypt.org/getting-started/  
  
