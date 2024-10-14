# Actividad Dns
Los comandos utilizados se mostrarán como título de segundo nivel y debajo su explicación

## cd /etc/bind
Con este comando nos movemos al directorio /ect/bind

## sudo nano /etc/bind/named.conf.local
Aqui modificamos el archivo añadiendo la zona que será nuestro dominio

## mkdir /etc/bind/zones
Creamos una carpeta en dicho directroio llamada zones

## cp db.local /etc/bind/zones/ejemplo.com.zone
Copiamos el archivo db.local en el directorio indicado

## sudo nano /etc/bind/zones/ejemplo.com.zone
Modificamos el archivo sustituyendo por nuestro localhost por nuestro dominio y asignando la ip fija
10.0.2.15

## service bind9 restart 
Reseteamos para comprobar si funciona

### nslookup ejemplo.com
Comprobamos que el proceso anterior hay funcionado correctamente

## dig ejemplo.com
El registro tipo A en DNS es uno de los tipos más comunes de registros que puedes encontrar al hacer consultas DNS, Asocia un nombre de dominio con una dirección IPv4.
Mientras que el registro NS define qué servidores DNS están autorizados para gestionar las consultas de un dominio.

## dig -x 10.0.2.15
El registro PTR en DNS se utiliza para realizar resoluciones inversas de DNS, es decir, convertir una dirección IP en un nombre de dominio. Este proceso es el inverso al típico en el que se convierte un nombre de dominio en una dirección IP

## Capturas
![Captura1](https://raw.githubusercontent.com/dlopnun1503/Despliegue/master/DNS/Actividades/Captura%20de%20pantalla%20(24).png)

![Captura2](https://raw.githubusercontent.com/dlopnun1503/Despliegue/master/DNS/Actividades/Captura%20de%20pantalla%20(25).png)

![Captura3](https://raw.githubusercontent.com/dlopnun1503/Despliegue/master/DNS/Actividades/Captura%20de%20pantalla%20(26).png)

![Captura4](https://raw.githubusercontent.com/dlopnun1503/Despliegue/master/DNS/Actividades/Captura%20de%20pantalla%20(28).png)