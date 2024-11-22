# Comandos utilizados

## Primera Parte
### 1: Crear un contenedor a partir de la imagen ubuntu:20.04
- docker run -it ubuntu:20.04 bash
- apt update
- apt install -y nano
- apt install -y vim
- apt install -y inetutils-tools
- apt install -y dnsutils
- adduser usuario

### 2: Crear la imagen personalizada y subirla a DockerHub
- docker commit <container_id> dlopnun1503/a61
- docker login
- docker push dlopnun1503/a61

## Segunda Parte
### 1: Crear un Dockerfile para la imagen php:7.4-apache
- nano Dockerfile y le añadimos: 
  
FROM php:7.4-apache


RUN apt-get update && \
    apt-get install -y nano git


COPY index.html /var/www/html/index.html
COPY info.php /var/www/html/info.php

- nano index.html
- nano info.php
- docker build -t dlopnun1503/a62 .

### 2: Subir la imagen a DockerHub
- docker push dlopnuun1503/a62


## Resultado
![Resultado]()




