
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


**
