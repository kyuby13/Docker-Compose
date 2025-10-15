#Clone

git clone https://github.com/flant/ovpn-admin.git
 
cd ovpn-admin/

# edit docker compose

nano docker-compose.yaml

tambahkan -> restart: unless-stopped

misalkan jadi seperti berikut :

 image: openvpn:local

 restart: unless-stopped

 command: /etc/openvpn/setup/configure.sh

Kemudian edit  OVPN_SERVER: "127.0.0.1:7777:tcp" -> dengan IP public atau domain mu

# Edit templates

nano  templates/client.conf.tpl

uncomment -> redirect-gateway def1

# kemudian build

docker-compose -p openvpn-master up -d

atau

./start.sh

#Opsi tambahan

iptables -t nat -A POSTROUTING -s 192.168.100.0/24 -o ens5 -j MASQUERADE

apt install -y iptables-persistent

netfilter-persistent save

timedatectl set-timezone Asia/Jakarta

echo "net.ipv4.ip_forward=1" | sudo tee -a /etc/sysctl.conf

sysctl -p

Open port public 7777 dan 8080

#Akses dashboard

IP:8080 / domain:8080

#Jika ada kendala di sisi client gak dapat internet

tambahkan di user.ovpn

redirect-gateway def1

dhcp-option DNS 1.1.1.1

dhcp-option DNS 8.8.8.8
