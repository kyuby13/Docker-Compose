#Akses WEb

http://<IP-server>:3000

Contoh: http://192.168.1.10:3000

#Izinkan Akses Remote di PostgreSQL

docker exec -it metabase_db bash

nano /var/lib/postgresql/data/postgresql.conf

#ubah baris ini

listen_addresses = '*'

#Edit juga file pg_hba.conf di lokasi yang sama (/var/lib/postgresql/data/pg_hba.conf):

Tambahkan di bagian paling bawah:

host all all 0.0.0.0/0 md5

#Restart Service

docker compose restart db

#Test koneksi dari luar

Host: <IP Server>   (contoh 192.168.3.4)

Port: 5432

Database: metabase

Username: metabase

Password: mysecret
