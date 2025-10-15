#Struktur (Wildcard SSL + Multi Nginx + PHP-FPM)

project/
│
├─ docker-compose.yml
│
├─ web1/
│   ├─ index.php
│   ├─ default.conf
│
├─ web2/
│   ├─ index.php
│   ├─ default.conf
│
├─ web3/
│   ├─ index.php
│   ├─ default.conf
│
└─ data/
    ├─ certs/
    ├─ vhost.d/
    └─ html/


#Contoh web1/default.conf

server {
    listen 80;
    server_name web1.games.com;

    root /usr/share/nginx/html;
    index index.php index.html;

    location / {
        try_files $uri $uri/ =404;
    }

    location ~ \.php$ {
        include fastcgi_params;
        fastcgi_pass php-web1:9000;
        fastcgi_index index.php;
        fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
    }
}

#Contoh web1/index.php

<?php
echo "Hello from Web1 (" . $_SERVER['SERVER_NAME'] . ")";
