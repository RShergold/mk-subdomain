# mk-subdomain
A small bash file for quickly creating new subdomains on the standard DigitalOcean 'LAMP on Ubuntu' server image.


## Overview

the script can do two things: 

1. prepare the file structure (just the way i like it) 
2. Create a directory for the new subdomain and tell apache about it

###1.


	./mk-subdomain init
	
will prepare your defult LAMP image for hosting multiple sites. This is done by moving the defult html document root from _/var/www/html_ to _/var/www/default/html_ 

This is where users who go to __yourdomain.com__ will be directed to. 

###2.

	./mk-subdomain subdomain
	
creates a html document directory at _/var/www/subdomain/html_ 

a new config file is created at _/etc/apache2/sites-available_ and symlinked to _/etc/apache2/sites-enabled_

this tells apache to direct requests from __subdomain.yourdomain.com__ to the new documents directory

