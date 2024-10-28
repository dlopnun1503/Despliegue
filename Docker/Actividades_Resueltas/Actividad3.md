# Comandos utilizados
### docker run -dit --name ubuntu ubuntu:18.04
Arrancamos el contenedor desde la imagen ubuntu:18.04 y le asignamos el nombre ubuntu

### docker stop ubuntu
Salimos del contenedor 

### docker ps -a | grep ubuntu
Verificamos que el contenedor se ha detenido 

### docker start ubuntu
Volver a iniciar el contenedor ubuntu

### docker ps | grep ubuntu
Verificar que está funcionando

### docker exec ubuntu cat /etc/os-release
Ver el contenido del archivo /etc/os-release desde fuera del contenedor

### Resultado
![Resultado](https://raw.githubusercontent.com/dlopnun1503/Despliegue/refs/heads/master/Docker/ResultadoActividad3.png)