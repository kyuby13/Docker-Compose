#Buat Directory

mkdir -p /opt/jenkins/{data,home}

cd /opt/jenkins

#Simpan docker-compose di derectory tersebut

#Ambil Password untuk Login Awal

docker exec jenkins cat /var/jenkins_home/secrets/initialAdminPassword

#Akses Web

http://<IP-server>:8080

