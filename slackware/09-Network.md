# Actividad 9.1

## Creamos el script ping.sh y escribimos el siguiente código
![Codigo]()

## Este código hace lo siguiete: 
- Se utiliza un bucle for para iterar a través de las direcciones IP desde 192.168.0.1 hasta 192.168.0.25.
- El comando ping se ejecuta con la opción -c 2, que envía 2 paquetes ICMP a cada dirección IP.
- &> /dev/null redirige tanto la salida estándar como el error a null para que no se muestre en pantalla.
- El $? evalúa el código de salida del comando ping. Si el valor es 0, significa que el host está activo.

## Le damos permisos con chmod +x ping.sh

## Lo ejecutamos con ./ping.sh
![ejecucion]()



# Actividad 10.1 User and system information

## ¿Cuántos intentos de inicio de sesión (exitosos y fallidos) ocurrieron en las últimas 48 horas?
Con el comando last vemos información sobre los inicios de sesión, que en las últimas 48 horas han sido dos el dia 21 de febrero.ç
Para ver los intentos fallidos utilizamos lastb, en mi caso solo aparece uno del día 7 de febrero.
![last]()
![lastb]()

## ¿Cuántos reinicios del sistema ocurrieron en las últimas 48 horas?
Con el comando last reboot vemos cuántos reinicios de sesión se han realizado, el último reinicio fue el 21 de febrero de 2025 a las 08:45 y aún está en ejecución.
El reinicio anterior fue el 14 de febrero de 2025 a las 12:50.
El siguiente reinicio antes de ese fue el 7 de febrero de 2025 a las 08:35.
![lastreboot]()



# Actividad 10.2  Symbolic and hard links

## 1. Crear el archivo extra_file y su enlace simbólico con los siguientes comandos:
touch extra_file
ln -s extra_file enlace_extra_file

## 2. Editar extra_file y comprobar el enlace simbólico
Si ejecutamos cat ~/unixstuff/links/extra_file_link, vemos el contenido del archivo extra_file.

## 3. Mover extra_file a otro directorio
Si movemos el archivo original y ejecutamos cat ~/unixstuff/links/extra_file_link, obtendremos un error porque el enlace simbólico ya no funciona

## 4. Mover de vuelta extra_file
Después de mover el archivo de vuelta, el enlace simbólico funcionará nuevamente, y al ejecutar cat ~/unixstuff/links/extra_file_link, veremos el contenido del archivo.

## 5. Eliminar extra_file_link
Después de eliminar el enlace simbólico con rm ~/unixstuff/links/extra_file_link, si intentas acceder a él con cat, obtendremos un error similar al del punto 3.

## 6. Recrear extra_file_link y eliminar extra_file
Después de recrear el enlace simbólico y eliminar el archivo original, al intentar acceder al enlace simbólico con cat, vemos un error porque el archivo original fue eliminado.

## 7. Repetir el ejercicio con enlaces duros.
Diferencias:
- Enlace simbólico: Si el archivo original se mueve o elimina, el enlace simbólico se rompe y muestra un error.
- Enlace duro: Si el archivo original se elimina, el enlace duro sigue funcionando, ya que ambos apuntan al mismo contenido del archivo.


