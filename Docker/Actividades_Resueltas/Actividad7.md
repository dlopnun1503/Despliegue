# Comandos utilizados
## Crear los volúmenes
- docker volume create volumen_datos
- docker volume create volumen_web
  
## Arrancar los contenedores
- docker run -d --name c1 -v volumen_web:/var/www/html php:7.4-apache
- docker run -d --name c2 -v volumen_datos:/var/lib/mysql -e MYSQL_ROOT_PASSWORD=admin mariadb

## Parar y borrar el contenedor c2 y eliminar el volumen
- docker stop c2
- docker rm c2
- docker volume rm volumen_datos


## Resultado
![Resultado]()