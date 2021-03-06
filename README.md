### Example Apache Server 
**************************
 - [unBlock Windows Problem Fix Apache Server](#unblock-windows-problem-fix-apache-server)
*********************************************************************************************
#### (Microsoft Windows 8.1 Pro) bit-x64 **``C:\Windows\System32\drivers\etc\hosts``**
```hosts
# Copyright (c) 1993-2009 Microsoft Corp.
#
# This is a sample HOSTS file used by Microsoft TCP/IP for Windows provided by MajorGeeks.Com
#
# This file contains the mappings of IP addresses to host names. Each
# entry should be kept on an individual line. The IP address should
# be placed in the first column followed by the corresponding host name.
# The IP address and the host name should be separated by at least one
# space.
#
# Additionally, comments (such as these) may be inserted on individual
# lines or following the machine name denoted by a '#' symbol.
#
# For example:
#
#      102.54.94.97     rhino.acme.com          # source server
#       38.25.63.10     x.acme.com              # x client host
# localhost name resolution is handled within DNS itself.
#	127.0.0.1       localhost
#	::1             localhost

# Home Sample
127.0.0.1       SamplePhpMyAdmin.com
127.0.0.1       SampleDirectoryServersNetwork.com

# Home Example
127.0.0.1       SampleAllServersNetwork.WordPress.com
127.0.0.1       SampleAllServersNetwork.com
127.0.0.1       SampleAdminServersNetwork.WordPress.com
127.0.0.1       SampleAdminServersNetwork.com

# Home Premium
127.0.0.1       www.HomePremiumSampleTube.Home.com
127.0.0.1       www.HomePremiumSampleServer.Home.com

# Home Manager
127.0.0.1       www.ManagerServer.com
127.0.0.1       www.ExampleServerRoot.com
127.0.0.1       www.DomainHosting.Manager.com
127.0.0.1       www.ServerSourceAddress.com

```
#### **``C:\Apache24\conf\``**
#### ****````WordPress.conf````****
```WordPress.conf
<VirtualHost *:80>
ServerName SampleAllServersNetwork.WordPress.com
ServerAdmin AdminMail@SampleAllServersNetwork.WordPress.Default.com
DocumentRoot "C:/Users/Credit/Documents/#Server(htdocs)(www)/WordPress/Home"
<Directory "C:/Users/Credit/Documents/#Server(htdocs)(www)/WordPress/Home">
# BEGIN WordPress 
 RewriteEngine On  
 RewriteBase /
 RewriteRule ^index\.php$ - [L]
 
# uploaded files
 RewriteRule ^([_0-9a-zA-Z-]+/)?files/(.+) wp-includes/ms-files.php?file=$2 [L]

# add a trailing slash to /wp-admin
 RewriteRule ^([_0-9a-zA-Z-]+/)?wp-admin$ $1wp-admin/ [R=301,L]
 RewriteCond %{REQUEST_FILENAME} -f [OR]
 RewriteCond %{REQUEST_FILENAME} -d
 RewriteRule ^ - [L]
 RewriteRule  ^[_0-9a-zA-Z-]+/(wp-(content|admin|includes).*) $1 [L]
 RewriteRule  ^[_0-9a-zA-Z-]+/(.*\.php)$ $1 [L]
 RewriteRule . index.php [L]
# END WordPress

AllowOverride None

</Directory>
</VirtualHost>
```

<!--
- [How to Solve Port 80 Problems When Running Apache](#how-to-solve-port-80-problems-when-running-apache)
- [How to fix Apache server error (Windows) | How to fix "Apache is not running"](#how-to-fix-apache-server-error-windows--how-to-fix-apache-is-not-running-)
-->

***
- [x] ``Example Apache Server (PHP) httpd.conf``
***

```httpd.conf
PHPIniDir "E:/ComposerDirectory/ComposerDirectory/PHP/(64-bit) 7.3.15/"
LoadModule php7_module "E:/ComposerDirectory/ComposerDirectory/PHP/(64-bit) 7.3.15/php7apache2_4.dll"

AddType application/x-httpd-php .php
```

***
- [x] ``Example Apache Server (Virtual Host) httpd.conf``
***

```httpd.conf
Listen 80

<VirtualHost *:80>
	ServerName localhost
  
	ServerAlias localhost
  ServerAdmin admin@localhost
		
    DocumentRoot "C:/Users/Credit/Documents/#Server(htdocs)(www)/@localhost"	
	<Directory "C:/Users/Credit/Documents/#Server(htdocs)(www)/@localhost">
        
	SSLOptions +StdEnvVars
	
    Options Indexes FollowSymLinks MultiViews
    AllowOverride All

</Directory>

ErrorDocument 500 /500.html
ErrorDocument 404 /404.html

</VirtualHost>



#Listen 8000
#<VirtualHost *:8000>

#	ServerName HomePremiumSampleTube.server.tv
#	ServerAlias HomePremiumSampleTube.server.tv
#   ServerAdmin admin@HomePremiumSampleTube.server.tv

		
#    DocumentRoot "C:/Users/Credit/Documents/#Server(htdocs)(www)/HomePremiumSampleTube/"	
#	<Directory "C:/Users/Credit/Documents/#Server(htdocs)(www)/HomePremiumSampleTube/">
        
#	SSLOptions +StdEnvVars
	
#    Options Indexes FollowSymLinks MultiViews
#    AllowOverride All


#</Directory>

#ErrorDocument 500 /500.html
#ErrorDocument 404 /404.html


#</VirtualHost>

<VirtualHost *:80>
	
	ServerName HomePremiumSample.com

	ServerAlias HomePremiumSample.com
    ServerAdmin admin@HomePremiumSample.com
	
    DocumentRoot "C:/Users/Credit/Documents/#Server(htdocs)(www)/HomePremiumSample"	
	<Directory "C:/Users/Credit/Documents/#Server(htdocs)(www)/HomePremiumSample">
        
	SSLOptions +StdEnvVars
	
    Options Indexes FollowSymLinks MultiViews
    AllowOverride All


</Directory>


ErrorDocument 500 /500.html
ErrorDocument 404 /404.html

</VirtualHost>

<VirtualHost *:80>
ServerName HomePremiumSampleTube.server.tv
ServerAlias HomePremiumSampleTube.server.tv
ServerAdmin admin@HomePremiumSampleTube.server.tv

		
    DocumentRoot "C:/Users/Credit/Documents/#Server(htdocs)(www)/HomePremiumSampleTube"	
	<Directory "C:/Users/Credit/Documents/#Server(htdocs)(www)/HomePremiumSampleTube">
        
	SSLOptions +StdEnvVars
	
    Options Indexes FollowSymLinks MultiViews
    AllowOverride All


</Directory>


ErrorDocument 500 /500.html
ErrorDocument 404 /404.html


</VirtualHost>


<VirtualHost *:80>
ServerName SampleMTDBNew.com

ServerAlias SampleMTDBNew.com
ServerAdmin admin@localhost

		
    DocumentRoot "C:/Users/Credit/Documents/#Server(htdocs)(www)/mtdb"	
	<Directory "C:/Users/Credit/Documents/#Server(htdocs)(www)/mtdb">
        
	SSLOptions +StdEnvVars
	
    Options Indexes FollowSymLinks MultiViews
    AllowOverride All


</Directory>



<IfModule php5_module>
LoadFile "E:/ComposerDirectory/ComposerDirectory/PHP/(64-bit) 5.6.0/php5ts.dll"
LoadModule php5_module "E:/ComposerDirectory/ComposerDirectory/PHP/(64-bit) 5.6.0/php5apache2_4.dll"
PHPIniDir "E:/ComposerDirectory/ComposerDirectory/PHP/(64-bit) 5.6.0/"

php_value session.cookie_httponly true
php_flag short_open_tag on
php_flag register_globals on

</IfModule>

</VirtualHost>


<VirtualHost *:80>
ServerAdmin root@localhost
ServerAlias SamplePhpMyAdmin.com

ServerName SamplePhpMyAdmin.com
DocumentRoot "C:/Users/Credit/Documents/#Server(htdocs)(www)/phpMyAdmin"

    
	#UseCanonicalName Off
  	
   	 # SSLCertificateFile "C:/Users/Credit/Documents/#Server(htdocs)(www)/SSL/crt/SamplePhpMyAdmin.com.crt"
	 # SSLCertificateKeyFile "C:/Users/Credit/Documents/#Server(htdocs)(www)/SSL/key/SamplePhpMyAdmin.com.key"
	
	<Directory "C:/Users/Credit/Documents/#Server(htdocs)(www)/phpMyAdmin">

	SSLOptions +StdEnvVars
	
    Options Indexes FollowSymLinks MultiViews
    AllowOverride All
	
    #Order Deny,Allow
    #Deny from all
    #Allow from 127.0.0.1 localhost ::1
	
</Directory>
</VirtualHost>



#LoadFile "E:/ComposerDirectory/ComposerDirectory/PHP/(64-bit) 5.6.0/php5ts.dll"

#LoadModule php5_module "E:/ComposerDirectory/ComposerDirectory/PHP/(64-bit) 5.6.0/php5apache2_4.dll"

#<IfModule php5_module>
#    PHPIniDir "E:/ComposerDirectory/ComposerDirectory/PHP/(64-bit) 5.6.0/"
#    <Location>
#       AddType text/html .php
#       AddHandler application/x-httpd-php .php
#    </Location>
#</IfModule>



#<IfModule php5_module>
#LoadModule php5_module "E:/ComposerDirectory/ComposerDirectory/PHP/(64-bit) 5.6.0/php5apache2_4.dll"
#ScriptAlias /php/"E:/ComposerDirectory/ComposerDirectory/PHP/(64-bit) 5.6.0/"
#AddType application/x-httpd-php .php .php5
#Action application/x-httpd-php "/PHP/php-cgi.exe"
#SetEnv PHPRC "E:/ComposerDirectory/ComposerDirectory/PHP/(64-bit) 5.6.0/"
#PHPIniDir "E:/ComposerDirectory/ComposerDirectory/PHP/(64-bit) 5.6.0/"
#</IfModule>



#<VirtualHost *:8080>
    #ServerAdmin admin@localhost
    #ServerName SamplePhpMyAdmin.com 
    #ServerAlias SamplePhpMyAdmin.com
    #DocumentRoot "C:/Users/Credit/Documents/#Server(htdocs)(www)/phpMyAdmin"
   
    #SSLCertificateFile "C:/wamp/bin/apache/apache2.4.9/conf/key/certificate.crt"
	#SSLCertificateKeyFile "C:/wamp/bin/apache/apache2.4.9/conf/key/private.key"
#</VirtualHost>


#<VirtualHost *:8080>
    #ServerAdmin admin@localhost
    #ServerName SamplePhpMyAdmin.com 
    #ServerAlias SamplePhpMyAdmin.com
    #DocumentRoot "C:/Users/Credit/Documents/#Server(htdocs)(www)/phpMyAdmin"

    #UseCanonicalName Off
	
    #ErrorLog "C:/Apache24/logs/ssl_error.log"
	#TransferLog "C:/Apache24/logs/ssl_access.log"


	#SSLCertificateFile "C:/Apache24/conf/key/certificate.crt"
	#SSLCertificateKeyFile "C:/Apache24/conf/key/private.key"
	
	
#<Directory "/phpMyAdmin">

#Options -Indexes FollowSymLinks ExecCGI
#AllowOverride None
#Order allow,deny

#Allow from all

#</Directory>
#</VirtualHost>


#openssl genrsa -out SamplePhpMyAdmin.com.key 2048
#openssl req -new -sha256 -key SamplePhpMyAdmin.com.key -out SamplePhpMyAdmin.com.csr
#openssl req -text -in SamplePhpMyAdmin.com.csr -noout


#openssl.exe genrsa 2048 > SamplePhpMyAdmin.com.key

# Default openssl.cnf
#openssl.exe req -new -key SamplePhpMyAdmin.com.key > SamplePhpMyAdmin.com.csr

#openssl rsa -in SamplePhpMyAdmin.com.pem -out SamplePhpMyAdmin.com.key
#openssl x509 -in SamplePhpMyAdmin.com.csr -out SamplePhpMyAdmin.com.crt -req -signkey SamplePhpMyAdmin.com.key -days 365



################################################################################

#openssl.cnf

################################################################################

#openssl.exe req -new -key SamplePhpMyAdmin.com.key -config "openssl.cnf" -out SamplePhpMyAdmin.com.csr

################################################################################

#openssl req -config "C:\openssl.cnf" -new -out SamplePhpMyAdmin.com.csr -keyout SamplePhpMyAdmin.com.pem

################################################################################


```

***
### [Select Package PHP extension](https://pecl.php.net/package)
***
### **``unblock example``** Apache Server Port:[80] Windows



***
## WordPress Example subdomain port 80 .htaccess
```.htaccess
RewriteEngine on
RewriteCond %{HTTP_HOST} ^www.wordpress.wp.com
RewriteRule ^(.*) http://www.wordpress.wp.com/PathToPageHere [P]
```

***
## WordPress subdomain port 80 .htaccess
```.htaccess
# Custom subdomain .htaccess port 80 WordPress

RewriteEngine on
RewriteCond %{HTTP_HOST} ^www.wordpress.wp.com$ [NC,OR]
RewriteCond %{HTTP_HOST} ^www.wordpress.wp.com$ 
RewriteCond %{REQUEST_URI} !wordpress/
RewriteRule (.*) /wordpress/$1 [L]

# End custom subdomain .htaccess port 80 WordPress
```
## WordPress subdomain port 8080 .htaccess
```.htaccess
# Custom subdomain .htaccess port 8080 WordPress

RewriteEngine On
RewriteCond %{SERVER_PORT} 8080
RewriteCond %{REQUEST_URI} !wordpress/
RewriteRule ^(.*)$ http://www.wordpress.wp.com:%{SERVER_PORT}/wordpress/$1 [R,L]

# End custom subdomain .htaccess port 8080 WordPress
```

***
## WordPress SSL + subdomain .htaccess
```.htaccess
# BEGIN HTTPS
<IfModule mod_rewrite.c>
RewriteEngine On
RewriteCond %{HTTPS} off
RewriteRule ^(.*)$ https://%{HTTP_HOST}%{REQUEST_URI} [L,R=301]
</IfModule>
# END HTTPS
```
***
## WordPress SSL + subdomain + maindomain .htaccess
```.htaccess
# Custom subdomain .htaccess SSL + WordPress
RewriteEngine On
RewriteCond %{HTTP_HOST} ^subdomain.maindomain.com$
RewriteCond %{REQUEST_URI} !^/subfolder/
RewriteRule ^(.*)$ /subfolder/$1
RewriteCond %{HTTP_HOST} ^subdomain.maindomain.com$
RewriteRule ^(/)?$ subfolder/index.php [L]
# End custom subdomain .htaccess

# Custom maindomain .htaccess WordPress
RewriteEngine On
RewriteBase /
RewriteCond %{HTTP_HOST} ^(www.)?maindomain.com$
RewriteRule ^index\.php$ - [L]
RewriteCond %{HTTP_HOST} ^(www.)?maindomain.com$
RewriteCond %{REQUEST_FILENAME} !-f
RewriteCond %{REQUEST_FILENAME} !-d
RewriteRule . /index.php [L]
# End custom maindomain .htaccess
```
***



***
## unBlock Windows Problem Fix Apache Server
### How to Solve Port 80 Problems When Running Apache 
#### ``How to fix Apache server error (Windows) | How to fix "Apache is not running" ``

<!-- ###### Fix unblock port:[80] on windows run Apache -->
***
## Windows Command Processor

```cmd
C:\Windows\System32\cmd.exe
```


## Fix unBlock Port:[80] on Windows Run Apache

``net stop was /y``

``net start was /y``

[Fix unblock port:[80] on windows run Apache](https://www.sitepoint.com/unblock-port-80-on-windows-run-apache/)
