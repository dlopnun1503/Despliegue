# 7.2 Running Apache

## 7.2.1 Motivo para reiniciar httpd tras cambios en la configuración
Cuando se realizan cambios en el archivo de configuración de Apache, el servidor debe reiniciarse para que los nuevos ajustes sean aplicados correctamente. Sin un reinicio, Apache seguiría funcionando con la configuración antigua.

## 7.2.2 Explicación del comando ps aux | grep httpd
- ps aux: Muestra todos los procesos en ejecución en el sistema, incluyendo aquellos de otros usuarios.
- grep httpd: Filtra los resultados de ps aux para mostrar solo las líneas que contienen "httpd".
- |: Es un operador de tubería que permite pasar la salida de un comando como entrada de otro.
- El comando completo muestra todos los procesos relacionados con Apache HTTP Server.

## Salida esperada:
- Si httpd está corriendo, aparecerá una o más líneas mostrando los procesos activos relacionados con Apache.
- Si httpd no está corriendo, el comando no devolverá ninguna salida.

## 7.2.3 Ejecutamos ps axl | egrep "httpd|PPID"
Se identificará el PPID en la columna correspondiente al proceso padre de Apache.

## Comando ejecutado
![comandoEjecutado](https://raw.githubusercontent.com/dlopnun1503/Despliegue/refs/heads/master/Capturas%20slackware/07-PHP/Ejecucion%20comando%207.2.png)



# 7.3 Creating HTMLfiles

## 7.3.1 Importancia de index.htm e index.html
Son archivos predeterminados que Apache carga cuando un usuario accede a un directorio sin especificar un archivo en la URL.

## 7.3.2 Verificación de permisos y propiedad de index.html
Ejecutamos ls -l index.html
Se mostrará la información de permisos, usuario y grupo propietario.

## ls -l index.html
![comandoEjecutado2](https://raw.githubusercontent.com/dlopnun1503/Despliegue/refs/heads/master/Capturas%20slackware/07-PHP/ls%20-l%20index.html.png)

## 7.3 Creación del archivo test.html y dibujo de la vista esperada
Creamos test.html
En un navegador, se espera ver un título "NSE Apache Lab", un encabezado y un párrafo con "En construcción!".

## Contenido añadido al fichero
![comandoFichero](https://raw.githubusercontent.com/dlopnun1503/Despliegue/refs/heads/master/Capturas%20slackware/07-PHP/ContenidoFichero.png)



# 7.4 Viewing HTML files using a terminalinterface

## 7.4.1 Diferencia entre CLI y GUI
- CLI es una interfaz basada en texto donde se ejecutan comandos.
- GUI es una interfaz visual con ventanas y botones.

## 7.4.2 Importancia de la dirección IP 127.0.0.1
Es la dirección de loopback usada para acceder al propio sistema local.

## 7.4.3 Visualización del archivo en Lynx
Ejecutamos lynx 127.0.0.1/test.html

## Visualización
![Visualizacion](https://raw.githubusercontent.com/dlopnun1503/Despliegue/refs/heads/master/Capturas%20slackware/07-PHP/7.4.3.png)

## 7.4.4 Visualización desde la máquina host
Obtener la IP de la máquina virtual con ifconfig o ip a
Acceder desde un navegador en Windows a http://10.0.2.15/test.html



# 7.5 Creating and viewing PHP files using a terminal interface

## 7.5.1 Función de phpinfo();
Muestra información detallada sobre la configuración de PHP y Apache.

## 7.5.2 Visualización del archivo en Lynx
Creamos un archivo nse.php
Ejecutamos lynx 127.0.0.1/nse.php para verlo

## Visualización
![Visualizacion2](https://raw.githubusercontent.com/dlopnun1503/Despliegue/refs/heads/master/Capturas%20slackware/07-PHP/7.5.2.png)



# 7.6  Exploring and adding an entry to the hosts file

## 7.6.1 Edición del archivo /etc/hosts
Abrimos /etc/hosts.
Agregamos la línea 127.0.0.1 www.example.com antes de # End of hosts.

## 7.6.2 Verificación de la configuración
Ejecutamos lynx www.example.com

## Visualización
![Visualizacion3](https://raw.githubusercontent.com/dlopnun1503/Despliegue/refs/heads/master/Capturas%20slackware/07-PHP/7.6.png)



# 7.7 Optional exercises

## 7.7.1 Crear un archivo index.php y determinar qué archivo se carga
Creamos un archivo index.php en el mismo directorio que test.html y nse.php, con el siguiente código PHP:
<?php
echo "<head><title>PHP test</title></head>\n";
echo "Current PHP version: " . phpversion();
?>
Cuando ejecutemos lynx 127.0.0.1 en la terminal, se cargará index.html por defecto. Esto sucede porque Apache prioriza servir archivos .html sobre los archivos .php, si está configurado de esta manera.

## ¿Cómo cambiar este comportamiento?
Para que se cargue index.php en lugar de index.html, podemos cambiar la configuración de DirectoryIndex en el archivo httpd.conf de Apache:
1. Abre el archivo httpd.conf
2. Busca la directiva DirectoryIndex
3. Modifica la línea que aparece para incluir index.php primero
4. Guarda los cambios y reinicia Apache para que la configuración tenga efecto.
   

## 7.7.2 Protección con contraseña de un directorio
### A. Crear el archivo de contraseñas
Para proteger con contraseña el directorio DocumentRoot, primero debemos crear un archivo que contenga los usuarios y contraseñas. Usamos el comando htpasswd para hacerlo.
Ejecutamos htpasswd -c /var/www/.htpasswd user
Esto creará un archivo .htpasswd en el directorio /var/www/ con el usuario user

### B.  Configurar la protección en httpd.conf
Para proteger el directorio DocumentRoot usando autenticación básica, abrimos el archivo httpd.conf y agrega la configuración adecuada.
1. Abrimos el archivo httpd.conf
2. Buscamos la sección que contiene la directiva y añadimos las siguientes líneas justo encima de la etiqueta </Directory>:
    - Order allow,deny
    - Allow from all
    
    - AuthType Basic
    - AuthName "Authorization required"
    - AuthUserFile /var/www/.htpasswd
    - Require valid-user
    
    - Order allow, deny
    - Allow from all
3. Guarda los cambios y reinicia Apache


### C. Verifica la protección con lynx
Ejecutamos lynx 127.0.0.1

   