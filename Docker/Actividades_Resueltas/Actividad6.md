# Comandos utilizados
- docker pull ubuntu:20.04 -> (Descargar imagen)

- docker inspect ubuntu:20.04 > info.txt -> (Obtener información de la imagen y guardar en info.txt)

- docker run --name modulo3 -d ubuntu:20.04 -> (Crear un contenedor llamado modulo3)

- docker ps -a -> (Verificar que el contenedor se ha creado)

- docker rmi ubuntu:20.04 -> (Intentar eliminar la imagen)

- docker rm -f modulo3 -> (Si falla, eliminar el contenedor modulo3)

- docker rmi ubuntu:20.04 -> (Ahora eliminar la imagen)
  
## Razonamiento
He descargado la imagen ubuntu:20.04 desde Docker Hub, luego obtuve su información detallada y la guardé en un archivo info.txt. Después, creé un contenedor llamado modulo3 a partir de esa imagen. Verifiqué que el contenedor se había creado correctamente. Al intentar borrar la imagen, no pude hacerlo porque estaba siendo utilizada por el contenedor. Para solucionarlo, eliminé el contenedor y luego pude borrar la imagen sin problemas.

## Resultado
![Resultado](https://raw.githubusercontent.com/dlopnun1503/Despliegue/refs/heads/master/Docker/Actividad6.png)