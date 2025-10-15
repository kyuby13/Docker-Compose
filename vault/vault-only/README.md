#RUN

docker compose up -d

#Masuk Ke Container

docker exec -it vault sh

vault login root

#akses UI

http://localhost:8200

Token login: root
