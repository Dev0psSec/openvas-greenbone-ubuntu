![alt](https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTiky2VU-AuvBnkohI4ekzVIDJwnrx8A_Ou0Q&s)

# Docker compose file for openvas greenbone with nginx providing extra tls layer



## generate the keys before 

`openssl req -x509 -newkey rsa:4096 -keyout serverkey.pem -out servercert.pem -nodes -subj '/CN=localhost' -addext 'subjectAltName = DNS:localhost' -days 31`

## change the dir for your certs in the docker-compose file

`secrets:`

`  server-cert:`

`    file: /etc/greenbone/cert/servercert.pem`

`  server-key:`

`    file: /etc/greenbone/cert/serverkey.pem`

## run it (on 9392 port)

`docker compose -f $docker-compose.yml -p greenbone-community-edition up -d`

## enjoy!
