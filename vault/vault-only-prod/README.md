#Buat Folder

mkdir -p vault-data vault-config certs

Simpan file vault.crt dan vault.key (SSL certificate dan private key) di dalam folder certs/.


#jalankan 

docker compose up -d

docker exec -it vault sh

#inisialiasi

vault operator init

#Unseal

vault operator unseal

#Login (gunakan salah satu root token dari hasil init):

vault login <root_token>

#akses UI

https://localhost:8200
