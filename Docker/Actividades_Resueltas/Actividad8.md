# Comandos utilizados
- mkdir saludo
  
- echo "<h1>Hola soy David Lopez Nunez</h1>" > saludo/index.html
  
- docker run -d --name c1 -p 8181:80 -v "$(pwd)/saludo":/var/www/html php:7.4-apache
  
- docker run -d --name c2 -p 8282:80 -v "$(pwd)/saludo":/var/www/html php:7.4-apache
  
- docker ps


## Razonamiento


## Resultado
![Resultado]()