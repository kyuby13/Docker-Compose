#Akses WEb

http://localhost:8080

Login dengan:

Username: admin

Password: admin123

#Tambah User

docker exec -it nagios bash

htpasswd /opt/nagios/etc/htpasswd.users namauserbaru

htpasswd /opt/nagios/etc/htpasswd.users yuby

docker restart nagios


#Batasi ROle User

docker exec -it nagios bash

/opt/nagios/etc/cgi.cfg

Cari Baris Berikut dan tambahkan user nya :

authorized_for_all_services=yuby,admin

authorized_for_all_hosts=yuby,admin

authorized_for_system_information=admin

authorized_for_configuration_information=admin

authorized_for_system_commands=admin

authorized_for_all_service_commands=admin

authorized_for_all_host_commands=admin

docker restart nagios

#Untuk menambahkan server Client

docker exec -it nagios bash

/opt/nagios/etc/objects/

docker restart nagios
