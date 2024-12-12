# Comandos utilizados
### Instalar Docker y Docker Compose
- sudo apt update
- sudo apt install -y docker.io docker-compose
- sudo systemctl start docker
- sudo systemctl enable docker

### Crear un directorio para MediaWiki
- mkdir mediawiki-docker
- cd mediawiki-docker

### crea el archivo docker-compose.yml con el siguiente contenido
version: '3.7'

services:
  db:
    image: mariadb:10.5
    container_name: mediawiki-db
    restart: always
    environment:
      MYSQL_ROOT_PASSWORD: rootpassword
      MYSQL_DATABASE: mediawiki
      MYSQL_USER: mediawiki
      MYSQL_PASSWORD: mediapassword
    volumes:
      - db_data:/var/lib/mysql

  mediawiki:
    image: mediawiki:latest
    container_name: mediawiki
    restart: always
    ports:
      - "8080:80"
    environment:
      MEDIAWIKI_DB_HOST: db
      MEDIAWIKI_DB_NAME: mediawiki
      MEDIAWIKI_DB_USER: mediawiki
      MEDIAWIKI_DB_PASSWORD: mediapassword
    depends_on:
      - db
    volumes:
      - mediawiki_data:/var/www/html

volumes:
  db_data:
  mediawiki_data:

### Iniciar los contenedores
- docker-compose up -d

### Sube el archivo LocalSettings.php al contenedor de MediaWiki
- docker cp LocalSettings.php mediawiki:/var/www/html/LocalSettings.php

### Reinicia el contenedor de MediaWiki
- docker-compose restart mediawiki

### Verificar la persistencia de datos
- docker-compose down
docker-compose up -d


## Razonamiento
El objetivo de la tarea es implementar un sistema de gestión de contenido basado en MediaWiki utilizando Docker Compose, asegurando que los datos sean persistentes tras reinicios. 

## Resultado
![Resultado](https://raw.githubusercontent.com/dlopnun1503/Despliegue/refs/heads/master/Docker/Fichero%20compose.png)
![Resultado1](https://raw.githubusercontent.com/dlopnun1503/Despliegue/refs/heads/master/Docker/Resultado%20compose.png)