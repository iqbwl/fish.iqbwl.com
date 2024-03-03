---
title: "Cara setup phpMyAdmin dengan Nginx"
date: 2023-05-16T13:02:14+07:00
draft: false # Set 'false' to publish
description: "phpMyAdmin is a free and open source administration tool for MySQL and MariaDB. As a portable web application written primarily in PHP, it has become one of the most popular MySQL administration tools, especially for web hosting services"
categories:
- Linux
tags:
- nginx
- phpmyadmin
layout: "simple"
---

Yang pertama, untuk phpmyadmin pada website resminya [phpmyadmin.net/downloads/](https://www.phpmyadmin.net/downloads/).

```bash
cd /var/www
 wget https://files.phpmyadmin.net/phpMyAdmin/5.2.1/phpMyAdmin-5.2.1-all-languages.zip
 unzip phpMyAdmin-5.2.1-all-languages.zip
 mv phpMyAdmin-5.2.1-all-languages phpmyadmin
```

Copy config.sample.inc.php
```bash
cp config.sample.inc.php config.inc.php
```

Kemudian buat server-block pada Nginx.
```bash
vim /etc/nginx/conf.d/phpmyadmin.conf
```

Masukan konfigurasi berikut:
```
server {
    listen 8000;
    server_name _;
    location / {
           root /var/www/phpmyadmin;
           index index.php;
           location ~ ^/(.+\.php)$ {
                   try_files $uri =404;
                   root /var/www/phpmyadmin;
                   fastcgi_pass php;
                   fastcgi_index index.php;
                   fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
                   include /etc/nginx/fastcgi_params;
           }
           location ~* ^/(.+\.(jpg|jpeg|gif|css|png|js|ico|html|xml|txt))$ {
                   root /var/www/phpmyadmin;
           }
    }
}
```

Jangan lupa konfigurasi juga php-fpm nya, `fastcgi_pass php;` ganti dengan socket atau listen dimana php-fpm berada.

Simpan dan restart Nginx, akses phpMyadmin melalui URL http://ip_address:8000/

Selesai..