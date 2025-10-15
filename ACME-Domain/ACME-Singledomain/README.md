#Struktur

project/
│
├─ docker-compose.yml
│
├─ web/
│   ├─ index.php
│   └─ default.conf
│
└─ data/
    ├─ certs/
    ├─ vhost.d/
    └─ html/

#File: web/default.conf

server {
    listen 80;
    server_name web.games.com;

    root /usr/share/nginx/html;
    index index.php index.html;

    location / {
        try_files $uri $uri/ =404;
    }

    location ~ \.php$ {
        include fastcgi_params;
        fastcgi_pass php-web:9000;
        fastcgi_index index.php;
        fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
    }
}

#File: web/index.php

<?php
echo "<h1>Hello from web.games.com!</h1>";
phpinfo();


