#Buat Direktory

mkdir temporal-setup && cd temporal-setup


#Jalankan

docker compose up -d


#Jika di cek container nya

docker ps

temporal-web

temporal-admin-tools

temporal

temporal-postgres

#Akses Via Web

http://localhost:8080

#Via CLI

docker exec -it temporal-admin-tools bash

- buat namespace

tctl namespace register default

