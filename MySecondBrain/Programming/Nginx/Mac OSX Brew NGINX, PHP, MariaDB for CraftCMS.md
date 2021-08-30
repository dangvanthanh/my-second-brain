# Mac OSX Brew NGINX/PHP/MariaDB for CraftCMS

## Prerequisites

Install NGINX, PHP, MariaDB, and Composer.
```
$ brew install nginx php mariadb composer
```

## MariaDB

Create a MariaDB configuration.
```
$ touch ~/.my.conf
```

Paste in the following, change to reflect your username, and save.
```
[client]
user=USERNAME
```

Start MariaDB.
```
$ brew services start mariadb
```

## NGINX

Edit the default configuration (`/usr/local/etc/nginx/nginx.conf`) to reflect the following, changing to match your username, and save.
```
user USERNAME;

worker_processes 1;

events {

  worker_connections 1024;

}

http {

  include mime.types;

  default_type application/octet-stream;

  log_format main '$remote_addr - $remote_user [$time_local] "$request" '
                  '$status $body_bytes_sent "$http_referer" '
                  '"$http_user_agent" "$http_x_forwarded_for"';

  sendfile on;

  tcp_nopush on;

  keepalive_timeout 65;

  gzip on;

  include conf.d/*;

}
```

Rename the "servers" directory to "conf.d":
```
$ mv /usr/local/etc/nginx/servers /usr/local/etc/nginx/conf.d
```

Start NGINX.
```
$ brew services start nginx
```

## PHP

Edit the default configuration (`/usr/local/etc/php/8.0/php-fpm.d/www.conf`) to reflect the following, changing to match your username and desired group (usually "admin"), and save.
```
user = USERNAME
group = GROUP
...
listen = /usr/local/var/run/php-fpm.sock
...
listen.owner = USERNAME
listen.group = GROUP
listen.mode = 0660
```

Start PHP-FPM.
```
$ brew services start php
```

## Craft

Create a new Craft CMS site on your desktop.
```
$ cd ~/Desktop
$ composer create-project craftcms/craft testsite
```

Create a database.
```
$ mysql
...
MariaDB [(none)]> create database testsite;
Query OK, 1 row affected (0.000 sec)
...
MariaDB [(none)]> exit
Bye
```

Create an NGINX configuration.
```
$ touch /usr/local/etc/nginx/conf.d/testsite.conf
```

Paste in the following, changing to reflect your username, and save.
```
# Craft

server {

  listen 8080;

  server_name testsite;

  root /Users/USERNAME/Desktop/testsite/web;

  access_log /usr/local/var/log/nginx/testsite-access.log;

  error_log /usr/local/var/log/nginx/testsite-error.log;

  location / {

    index index.php;

    try_files $uri $uri/ @craft;

  }

  location @craft {

    rewrite ^(.*) /index.php?$1 last;

  }

  location ~ \.php$ {

    include /usr/local/etc/nginx/fastcgi_params;

    #fastcgi_pass unix:/usr/local/var/run/php-fpm.sock;
	#fastcgi_pass 127.0.0.1:9000;

    fastcgi_index index.php;

    fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;

  }

}
```

Restart NGINX.
```
$ brew services restart nginx
```

Setup Craft, making sure to use "mysql" as your database and your username for the MariaDB user.
```
$ cd ~/Desktop
$ ./craft setup
```

Edit "/etc/hosts" to add a new localhost alias for "testsite".
```
127.0.0.1 localhost testsite
```

Visit http://testsite:8080 in your browser to test.