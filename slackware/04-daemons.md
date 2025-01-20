# 4.1  Exploring currently running processes

## Encontrar el número total de procesos en ejecución
ps aux | wc -l

## Identificar los 10 procesos más intensivos en uso de CPU
top

## Para mostrar los procesos de manera ordenada por el uso de CPU
ps aux --sort=-%cpu | head -n 11

## Explicación y descripción
Una vez que tengas la lista de los 10 procesos más intensivos en uso de CPU, consulta sus nombres y búscalos para describirlos brevemente.
Por ejemplo:
- Proceso A (PID 1234): Navegador web, responsable de manejar las pestañas y procesos de interfaz de usuario.
- Proceso B (PID 5678): Sistema de base de datos, gestionando múltiples conexiones y transacciones.
- .....
  
## Resultado 4.1 
![Resultado4.1]()



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
![Resultado4.2]()



# 4.3 Exploring UNIX signals

## Ejecutamo kill -l
kill -l

## Tabla 4.3
![Tabla4.3]()

## kill -l
![comando]()



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
![Resultado4.4.1]()


## 2. Deshabilitar FTP

## Editar nuevamente /etc/inetd.conf para deshabilitar FTP
### Comentamos la línea
#ftp    stream  tcp  nowait  root  /usr/sbin/tcpd  vsftpd

## Reiniciar inetd
sudo systemctl restart inetd

## Comprobar los cambios
ftp localhost

## Resultado 4.4.2
![Resultado4.4.2]()


## 3.¿Qué son SFTP y SSH? ¿Por qué no se recomienda usar Telnet?
- SFTP: Es un protocolo para transferir archivos que opera sobre SSH. Proporciona seguridad mediante encriptación, lo que protege las credenciales y los datos transferidos de interceptaciones.
- SSH: Es un protocolo que permite acceder y controlar un sistema de manera remota, utilizando encriptación para garantizar la seguridad en la comunicación.

No se recomienda usar telnet por: 
- Transmisión de datos sin encriptar
- Falta de autenticación fuerte
- Sustitución moderna