
## Security Http Header Settings ##
---

**Hide Server Name in Http Header**
> This is Required to hide the http header for ex.(Apache) from http header that would actually hide the Server Used in your Production

    //Install the lib apache modsecurity settings for ubuntu apache2 server
    apt-get install libapache2-modsecurity

    //Enable the security2 module
    sudo a2enmod security2

    //Add The Below Code in the Configuration File of apache which is enabled for serviing
    // Note: Dont add it in VirtualHost Context
    
    <IfModule security2_module>
        SecRuleEngine on
        ServerTokens Full
        SecServerSignature "None"
    </IfModule>


**Hide Web server Version From Http header**
> This is required toi hide the version used of the web server in the http header for security from any emtity who fing the information useful to Trespass the web server

    // Add these Lines in the apache Conf file to hide the version of web server used
    ServerTokens Prod
    ServerSignature Off


**Add X-XSS Protection for Server to securing form XSS Attacks By adding the Lines**
> By default / or By requirement the X-XSS Protection can be or be set to 0. Setting this Flag to 0 disable the protection to XSS Attacks. WE have to set the flag to 1.


    // Add below Line in the Apache  conf file to do so
    // Note: Please Add these Lines Outside the VirtualHost scope
    Header set X-XSS-Protection 1;mode=block

---
**X-Content-Type-Options Header**

---

The X-Content-Type-Options header is used to protect against MIME sniffing vulnerabilities. These vulnerabilities can occur when a website allows users to upload content to a website however the user disguises a particular file type as something else. This can give them the opportunity to perform cross-site scripting and compromise the website.

Unfortunately, the X-Content-Type-Options: nosniff header does not protect against all sniffing-related vulnerabilities. 

    // Add the Below Line the Configuration File of Apache
    Header set X-Content-Type-Options nosniff


**


Header set Content-Security-Policy "frame-ancestors 'none';"


Header set X-Frame-Options SAMEORIGIN