---
layout: post
title: Install Ghost with Nginx and MySQL
excerpt: ""
tags: [howto, linux, ghost, blog]
categories: howto
comments: true
guid: urn:uuid:d7ae1475-8a7a-476b-a260-24bbb61c74ce
---

[1]: http://0v.org/installing-ghost-on-ubuntu-nginx-and-mysql/
[2]: http://support.ghost.org/installing-ghost-linux/
[3]: https://github.com/joyent/node/wiki/Installing-Node.js-via-package-manager
[4]: http://mgarratt.co.uk/setting-up-ghost/
[5]: http://www.codelitt.com/blog/deploy-ghost-blog-on-ubuntu-server-and-serve-it-to-subdirectory-using-nginx/
[6]: https://github.com/nodejitsu/forever
[7]: http://docs.ghost.org/installation/deploy/

The steps I installed Ghost blog on Linode with Debian 7.5

###Prepare
~~~
apt-get update
apt-get upgrade
apt-get install -y build-essential
~~~

###Installing Nginx
~~~
apt-get install nginx
~~~

###Install Node.js

>Based on [here](3)

Setup with Debian (as root):

~~~
curl -sL https://deb.nodesource.com/setup | sudo bash -
~~~

Then install with Debian (as root):

~~~
apt-get install -y nodejs nodejs-legacy
~~~

###Install MySQL

~~~
apt-get install mysql-client mysql-server
~~~

###Secure MySQL

~~~
mysql_secure_installation
~~~

###Restart MySQL

~~~
/etc/init.d/mysql restart
~~~

or

~~~
service mysql restart
~~~

Using MySQL `mysql -u root -p` to setup database:

~~~
CREATE DATABASE YOUR_DATABASE;

CREATE USER 'YOUR_USERNAME' IDENTIFIED BY 'YOUR_PASSWORD';

GRANT ALL PRIVILEGES ON YOUR_DATABASE.* TO 'YOUR_USERNAME';

exit
~~~

###Install Ghost

>Based on [here](2)

created `/var/www/ghost` as ghost folder

~~~
mkdir -p /var/www/
cd /var/www/
curl -L https://ghost.org/zip/ghost-latest.zip -o ghost.zip
unzip -uo ghost.zip -d ghost
cd /var/www/ghost
~~~

Then setup ghost environment

~~~
npm install --production
npm install mysql
npm install forever -g
~~~

###Setup Ghost

Copy over the example config file and then edit it

~~~
cp config.example.js config.js

vim /var/www/ghost/config.js
~~~

Change production default url to your domain and setup MySQL database

~~~
url: 'http://YOUR_DOMAIN',
~~~


~~~
database: {
	client: 'mysql',
	connection: {
		host: 'localhost',
		user: 'YOUR_USERNAME',
		password: 'YOUR_PASSWORD',
		database: 'YOUR_DATABASE',
		charset: 'utf8'
	}
},
~~~


###Run Ghost as background process

Fix all permission

~~~
chown -R www-data:www-data /var/www/ghost
~~~

Then run ghost as background process by [forever](6) (you can find other deply methods in [here](7))

~~~
NODE_ENV=production forever start index.js
~~~

###Setup Nginx

~~~
vim /etc/nginx/sites-available/ghost
~~~

~~~
server {
    listen 80;

    server_name example.com www.example.com;

    location / {
        proxy_redirect		off;
        proxy_set_header	X-Real-IP         $remote_addr;
        proxy_set_header	X-Forwarded-For   $proxy_add_x_forwarded_for;
        proxy_set_header	Host              $http_host;
        proxy_set_header	X-NginX-Proxy     true;

        proxy_pass			http://127.0.0.1:2368;
    }
}
~~~

#Enable this site

~~~
ln -s /etc/nginx/sites-available/ghost /etc/nginx/sites-enabled/ghost
~~~

#Restart nginx

~~~
/etc/init.d/nginx restart
~~~

###Open Ghost

Now you can check `http://YOUR_DOMAIN` to see ghost in there.

Login `http://YOUR_DOMAIN/ghost` to setup your account.