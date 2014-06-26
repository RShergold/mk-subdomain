# mk-subdomain
A small bash file for quickly creating new subdomains on the standard DigitalOcean 'LAMP on Ubuntu' server image.

I'm presuming:

1. you have a server set up on DigitalOcean
2. you have already configured your domain name for this server

## How to use
***

###1 - prepare your DNS

Make sure you have a wildcard ( * asterix ) CNAME entry in your DNS settings (in DigitalOcean). this will make sure all subdomains are correctly routed to your server.

![alt tag](http://i.imgur.com/theoTrq.png)

You'll have to wait a while for the DNS update to propagate. 

You'll know this is working when __yourdomain.com__, __www.yourdomain.com__, __foo.yourdomain.com__  all show the same page.

###2 - download the script



ssh into your server and from the home directory download the script:
	
	wget https://raw.githubusercontent.com/RShergold/mk-subdomain/master/mk-subdomain
	

then make it executable:

	chmod +x mk-subdomain
	
###3 - tell the script what your domain name is

The script needs to know your domain name. replace __your_domain_here__ with your actual domain below

	sed -i "s|example.com|your_domain_here|g" mk-subdomain

###4 - move the defult documents directory (optional)

	./mk-subdomain init

This moves the standard directory for __yourdomain.com__ from /var/www/html to /var/www/default/html

###5 - make a new subdomain

now whenever you wish to create a new subdomain just do

	./mk-subdomain subdomainname
	
this creates __subdomainname.yourdomain.com__ and a documents directory at /var/www/subdomainname/html
