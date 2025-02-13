# 4.1  Exploring currently running processes

## Encontrar el número total de procesos en ejecución
ps aux | wc -l

## Identificar los 10 procesos más intensivos en uso de CPU
top

## Para mostrar los procesos de manera ordenada por el uso de CPU
ps aux --sort=-%cpu | head -n 11

## Explicación y descripción
Una vez que tengas la lista de los 10 procesos más intensivos en uso de CPU, consulta sus nombres y búscalos para describirlos brevemente.
- PID 1234: Navegador web, responsable de manejar las pestañas y procesos de interfaz de usuario.
- PID 5678: Sistema de base de datos, gestionando múltiples conexiones y transacciones.
- PID 91011: Se encarga de manejar solicitudes HTTP y entregar contenido web, como páginas HTML, imágenes, etc.
- PID 1213: Aplicación Java que maneja aplicaciones o servidores de backend, como plataformas de mensajería, sistemas de procesamiento de pagos, o cualquier otro programa intensivo que corre sobre la JVM
- PID 1415: El gestor de ventanas es responsable de manejar la interfaz de usuario en entornos gráficos.
- PID 1617: Usado para reproducir videos o manejar procesos multimedia.
- PID 1819: Los procesos relacionados con la seguridad escanean constantemente archivos y actividades del sistema.
- PID 2021: Se utiliza para realizar resoluciones de nombres de dominio, y puede experimentar alta carga si está realizando consultas extensas de DNS o gestionando tráfico elevado.
- PID 2223: Aplicaciones de análisis de datos o modelado predictivo a menudo requieren una gran cantidad de poder de procesamiento.
- PID 2425: El gestor de actualizaciones verifica, descarga e instala actualizaciones.
## Resultado 4.1 
![Resultado4.1](https://raw.githubusercontent.com/dlopnun1503/Despliegue/refs/heads/master/Capturas%20slackware/04-daemons/4.1.png)



# 4.2 Exploring network processes

## Ejecutamos el comando nmap después de instalarlo
sudo apt install nmap 
sudo nmap localhost

## Procesos comunes
- 22/tcp (ssh): Permite acceder de manera remota al sistema con una conexión segura y encriptada.
- 80/tcp (http): Utilizado para alojar páginas web accesibles a través de un navegador.
- 3306/tcp (mysql): Puerto de la base de datos MySQL, comúnmente utilizado por aplicaciones web o servicios que necesitan gestionar datos estructurados.
- 443/tcp (https): Puerto utilizado para servir contenido web en conexiones seguras HTTPS

## Resultado 4.2
![Resultado4.2](https://raw.githubusercontent.com/dlopnun1503/Despliegue/refs/heads/master/Capturas%20slackware/04-daemons/4.2.png)



# 4.3 Exploring UNIX signals

## Ejecutamo kill -l
kill -l

## Tabla 4.3
![Tabla4.3](https://raw.githubusercontent.com/dlopnun1503/Despliegue/refs/heads/master/Capturas%20slackware/04-daemons/tabla4.3.png)

## kill -l
![comando](https://raw.githubusercontent.com/dlopnun1503/Despliegue/refs/heads/master/Capturas%20slackware/04-daemons/kill%20-l.png)



# 4.4 Processes and networking

## 1.Configurar FTP y Telnet

## Comprobar que el usuario bob existe
cat /etc/passwd | grep bob

## Editar el archivo /etc/inetd.conf para habilitar FTP y Telnet
sudo nano /etc/inetd.conf

## Reiniciar inetd
sudo systemctl restart inetd

## Prueba de FTP
ftp localhost

## Iniciamos sesión como bob
## Subir un archivo
put archivo.txt

## Descargar un archivo
get archivo.txt

## Renombrar un archivo
rename archivo.txt nuevo_nombre.txt

## Eliminar un archivo
delete archivo.txt

## Prueba de telnet
telnet localhost

## Resultado 4.4.1
![Resultado4.4.1](https://raw.githubusercontent.com/dlopnun1503/Despliegue/refs/heads/master/Capturas%20slackware/04-daemons/put%20archivo.txt.png)


## 2. Deshabilitar FTP

## Editar nuevamente /etc/inetd.conf para deshabilitar FTP
### Comentamos la línea
#ftp    stream  tcp  nowait  root  /usr/sbin/tcpd  vsftpd

## Reiniciar inetd
sudo systemctl restart inetd

## Comprobar los cambios
ftp localhost

## Resultado 4.4.2
![Resultado4.4.2](https://raw.githubusercontent.com/dlopnun1503/Despliegue/refs/heads/master/Capturas%20slackware/04-daemons/Error%20ftp.png)

### En este caso encontramos el error 421 de servicio no disponible ya que hemos comentado la linea de ftp


## 3.¿Qué son SFTP y SSH? ¿Por qué no se recomienda usar Telnet?
- SFTP: Es un protocolo para transferir archivos que opera sobre SSH. Proporciona seguridad mediante encriptación, lo que protege las credenciales y los datos transferidos de interceptaciones.
- SSH: Es un protocolo que permite acceder y controlar un sistema de manera remota, utilizando encriptación para garantizar la seguridad en la comunicación.

No se recomienda usar telnet por: 
- Transmisión de datos sin encriptar
- Falta de autenticación fuerte
- Sustitución moderna