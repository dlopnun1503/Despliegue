# Comandos utilizados
- mkdir saludo
  
- echo "<h1>Hola soy David Lopez Nunez</h1>" > saludo/index.html
  
- docker run -d --name c1 -p 8181:80 -v "$(pwd)/saludo":/var/www/html php:7.4-apache
  
- docker run -d --name c2 -p 8282:80 -v "$(pwd)/saludo":/var/www/html php:7.4-apache
  
- docker ps


## Razonamiento
Usamos bind mounts para lograr persistencia de datos entre el sistema de archivos de la máquina anfitriona y los contenedores Docker. Esto significa que cualquier cambio que hagamos en los archivos de la carpeta saludo en la máquina anfitriona se reflejará de inmediato en ambos contenedores. 
Podemos acceder a la misma página web en cada contenedor, pero a través de distintas rutas, lo cual nos permite probar cómo se mantiene el contenido constante en ambos contenedores.

## Resultado
![Resultado](https://raw.githubusercontent.com/dlopnun1503/Despliegue/refs/heads/master/Docker/Comandos%20Act8.png)