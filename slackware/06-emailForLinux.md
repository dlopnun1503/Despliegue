# 6.1 Sending email using mail

## Creamos un archivo mensaje.txt para enviarlo a bob
echo "Archivo para bob." > mensaje.txt

## Enviamos el mail a bob
mail -s "Mensaje de prueba" bob@localhost < mensaje.txt

## Explicación del comando echo "Welcome to Network Computer Systems" | mail -s "Hello world" bob@anglia.bryant -c smith@anglia.bryant -b root@anglia.bryant
- echo "Welcome to Network Computer Systems": Genera el mensaje de correo con ese contenido.
- |: Redirige la salida del echo al comando mail.
- mail -s "Hello world": Envia un correo con el asunto "Hello world".
- bob@anglia.bryant: Destinatario principal del correo.
- -c smith@anglia.bryant: Envía una copia del correo a smith@anglia.bryant
- -b root@anglia.bryant: Envía una copia oculta del correo a root@anglia.bryant

## Mail enviado
![MailEnviado](https://raw.githubusercontent.com/dlopnun1503/Despliegue/refs/heads/master/Capturas%20slackware/06-Linux/Correo%20enviado.png)



# 6.2  Checking email

## Iniciamos sesión como bob
su bob

## Ejecutamos mail para ver los mail recibidos
mail

## Podemos ver como bob tiene dos mails recibidos del viernes 31 de enero a las 9:01 y 9:03 por David Lopez Nunez, ambos con el mismo asunto
![MailsRecibidos](https://raw.githubusercontent.com/dlopnun1503/Despliegue/refs/heads/master/Capturas%20slackware/06-Linux/Verificaci%C3%B3n%20correos.png)



# 6.3 Exploring mail

## 1. Operaciones básicas en mail

### Ejecutamos mail y seleccionamos un número de mensaje para leerlo
### Dentro de mail ejecutamos el siguiente comando para responder un mensaje
r numeroMensaje

### Envíamos un nuevo mail ahora de bob a dlopnun1503
mail -s "Asunto" dlopnun1503@localhost

### Borramos un mensaje
d numeroMensaje

### Guradar un mensaje
s numeroMensaje nombreArchivo

### Podemos ver el mensaje tras ejecutar r numeroMensjae y como después al ejecutar d numeroMensaje pone que tengo 0 mails
![6.3.1](https://raw.githubusercontent.com/dlopnun1503/Despliegue/refs/heads/master/Capturas%20slackware/06-Linux/6.3.1.png)



## 2. Contenido de /var/spool/mail/ y sus implicaciones de seguridad
Este directorio contiene los buzones de correo de los usuarios. Cada usuario tiene un archivo con su nombre, donde se almacenan sus correos electrónicos.
Implicaciones de seguridad:
- Si los archivos tienen permisos incorrectos, otros usuarios pueden leer correos privados.
- Se recomienda que solo el usuario propietario y root tengan acceso a su buzón.



## 3. Enviar un correo a bob@localhost desde tu_nombre@localhost usando Telnet en el puerto 25

### Conectámos al servidor SMTP local
telnet localhost 25

### Ejecutamos el siguiente comando para enviar el mail con telnet
HELO localhost
MAIL FROM:<dlopnun1503@localhost>
RCPT TO:<bob@localhost>
DATA
Subject: Prueba SMTP

Mail usando Telnet.
.
QUIT

### Resultado
![6.3.3](https://raw.githubusercontent.com/dlopnun1503/Despliegue/refs/heads/master/Capturas%20slackware/06-Linux/Mail%20con%20telnet.png)



## 4. Habilitar POP3 en Slackware
- Editar /etc/inetd.conf y buscar la línea que menciona pop3.
- Si está comentada, descomentarla.
- Guardar los cambios y reiniciar inetd.



## 5. Conectarse al servidor POP3 desde la máquina Windows

### Accedemos a pop3
telnet ip_del_servidor 110

### Ejecutamos
USER bob
PASS contraseñaBob
LIST
RETR numeroMensaje
QUIT



## 6. Puertos usados por SMTP y POP3
- SMTP usa el puerto 25 (envío de correos).
- POP3 usa el puerto 110 (recepción de correos).



#  6.4 Optional exercises
## 1. ¿Qué es IMAP? Diferencias entre POP3 e IMAP
IMAP es un protocolo de correo electrónico que permite a los usuarios acceder a sus mensajes almacenados en un servidor de correo remoto. A diferencia de POP3, IMAP permite gestionar el correo directamente en el servidor sin necesidad de descargarlo completamente en el dispositivo del usuario.
IMAP es más útil para quienes necesitan acceder a su correo desde diferentes dispositivos, mientras que POP3 es más eficiente para quienes prefieren descargar y almacenar sus correos en una sola computadora.

## 2. ¿Qué es el cifrado PGP y cómo funciona?
PGP es un sistema de cifrado utilizado para proteger correos electrónicos y archivos mediante criptografía de clave pública. Su objetivo es garantizar la confidencialidad, integridad y autenticidad de los datos.
PGP utiliza un sistema de clave pública y clave privada para cifrar y descifrar mensajes:
- Generación de claves: Cada usuario tiene un par de claves
- Cifrado del mensaje
- Cifrado del mensaje

Beneficios de PGP:
- Confidencialidad: Solo el destinatario puede leer el mensaje.
- Autenticidad: La firma digital garantiza que el mensaje proviene del remitente legítimo.
- Integridad: Asegura que el contenido no ha sido modificado durante la transmisión.