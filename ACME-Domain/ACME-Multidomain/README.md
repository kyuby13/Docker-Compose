#versi lengkap 

yang pakai Nginx + PHP-FPM per domain, tetap dengan nginx-proxy + acme-companion biar semua domain otomatis HTTPS tanpa ribet.

Cocok buat use case kamu web1.games.com, web2.games.com, dan web3.games.com — masing-masing punya konten HTML/PHP sendiri.

#Struktur Folder

Pastikan struktur folder kamu seperti ini:


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

#File: web1/default.conf

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

#File: web1/index.php

<?php
phpinfo();

#Pointing domain ke IP server

web1.games.com → IP server
web2.games.com → IP server
web3.games.com → IP server

#Jalankan

docker compose up -d

docker logs nginx-proxy-acme
