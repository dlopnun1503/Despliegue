# Comandos utilizados
- docker pull ubuntu:20.04 -> (Descargar imagen)

- docker inspect ubuntu:20.04 > info.txt -> (Obtener información de la imagen y guardar en info.txt)

- docker run --name modulo3 -d ubuntu:20.04 -> (Crear un contenedor llamado modulo3)

- docker ps -a -> (Verificar que el contenedor se ha creado)

- docker rmi ubuntu:20.04 -> (Intentar eliminar la imagen)

- docker rm -f modulo3 -> (Si falla, eliminar el contenedor modulo3)

- docker rmi ubuntu:20.04 -> (Ahora eliminar la imagen)

## Resultado
![Resultado](https://raw.githubusercontent.com/dlopnun1503/Despliegue/refs/heads/master/Docker/Actividad6.png)