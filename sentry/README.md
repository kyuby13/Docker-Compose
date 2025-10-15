#Clone Repo dan setup

git clone https://github.com/getsentry/self-hosted.git

cd self-hosted

./install.sh


#jalankan

docker compose up -d

#akses

http://localhost:9000 | http://<IP_SERVER>:9000


Login pertama kali dengan akun admin yang dibuat selama proses install.sh

#update versi terbaru

git pull

./install.sh

docker compose up -d



