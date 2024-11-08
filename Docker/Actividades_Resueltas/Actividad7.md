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

## Razonamiento
Creamos dos volúmenes, volumen_datos y volumen_web, para persistir los datos fuera de los contenedores. A continuación, arrancamos los dos contenedores: uno con la imagen php:7.4-apache y otro con mariadb, montando los volúmenes en las rutas correspondientes para asegurar que los datos y archivos se almacenen de manera persistente.
El contenedor c1 sirve un entorno web con PHP y Apache, y el contenedor c2 ejecuta MariaDB, con la contraseña de root configurada. Tras ello, se detuvo y eliminó el contenedor c2, lo que permitió borrar el volumen volumen_datos.

## Resultado
![Resultado](https://raw.githubusercontent.com/dlopnun1503/Despliegue/refs/heads/master/Docker/Actividad7.png)