# Comandos utilizados
- docker run -d --name web -p 8181:80 php:7.3-apache

- echo "<h1>HOLA SOY DavidLopezNunez</h1>" > index.html

- echo "<?php phpinfo(); ?>" > index.php
  
- docker cp index.html web:/var/www/html/index.html
  
- docker cp index.php web:/var/www/html/index.php
  
- docker run -d --name bbdd -p 3336:3306 \
    -e MARIADB_ROOT_PASSWORD=root \
    -e MARIADB_DATABASE=prueba \
    -e MARIADB_USER=invitado \
    -e MARIADB_PASSWORD=invitado \
    mariadb

- docker ps


## Resultado
![Resultado](https://raw.githubusercontent.com/dlopnun1503/Despliegue/refs/heads/master/Docker/Actividad4.png)