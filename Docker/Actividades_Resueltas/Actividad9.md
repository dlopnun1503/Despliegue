# Comandos utilizados

## 1: Crear las redes
### Red 1
- docker network create \
--driver bridge \
--subnet=172.28.0.0/16 \
--gateway=172.28.0.1 \
red1

### Red 2
- docker network create \
--driver bridge \
red2


## 2: Crear y configurar los contenedores
### Contenedor u1 conectado a red1
- docker run -dit \
--name u1 \
--hostname host1 \
--network red1 \
--ip 172.28.0.10 \
ubuntu:20.04
- docker exec -it u1 bash
- apt update && apt install -y inetutils-ping
exit

### Contenedor u2 conectado a red2
- docker run -dit \
--name u2 \
--hostname host2 \
--network red2 \
ubuntu:20.04
- docker exec -it u2 bash
- LO COPIAMOS DENTRO DEL CONTENEDOR: apt update && apt install -y inetutils-ping
exit


## 3: Hacer que ambos contenedores se vean
### Habilitar reenvío de paquetes en el host
- sysctl -w net.ipv4.ip_forward=1

### Configurar reglas de iptables
- iptables -I FORWARD -i br-<ID_red1> -o br-<ID_red2> -j ACCEPT
- iptables -I FORWARD -i br-<ID_red2> -o br-<ID_red1> -j ACCEPT

- docker network inspect red1
- docker network inspect red2


## 4: Verificar la conectividad
- docker exec -it u1 bash
- ping <IP_de_u2>
- docker exec -it u2 bash
- ping 172.28.0.10


## Resultado
![Resultado](https://raw.githubusercontent.com/dlopnun1503/Despliegue/refs/heads/master/Docker/Act9.png)
