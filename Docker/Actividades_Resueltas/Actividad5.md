# Comandos utilizados
- docker inspect -f '{{range.NetworkSettings.Networks}}{{.IPAddress}}{{end}}' web

- docker port web

- docker inspect -f '{{range.NetworkSettings.Networks}}{{.IPAddress}}{{end}}' bbdd

- docker port bbdd

- docker inspect -f '{{range.NetworkSettings.Networks}}{{.IPAddress}}{{end}}' web
  
- docker port web
  
- docker inspect -f '{{range.NetworkSettings.Networks}}{{.IPAddress}}{{end}}' bbdd

- docker port bbdd


## Resultado
![Resultado](https://raw.githubusercontent.com/dlopnun1503/Despliegue/refs/heads/master/Docker/Actividad5.png)