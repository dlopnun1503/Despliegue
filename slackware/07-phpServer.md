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
![comandoEjecutado]()



# 7.3 Creating HTMLfiles

## 7.3.1 Importancia de index.htm e index.html
Son archivos predeterminados que Apache carga cuando un usuario accede a un directorio sin especificar un archivo en la URL.

## 7.3.2 Verificación de permisos y propiedad de index.html
Ejecutamos ls -l index.html
Se mostrará la información de permisos, usuario y grupo propietario.

## ls -l index.html
![comandoEjecutado2]()

## 7.3 Creación del archivo test.html y dibujo de la vista esperada
Creamos test.html
En un navegador, se espera ver un título "NSE Apache Lab", un encabezado y un párrafo con "En construcción!".

## Contenido añadido al fichero
![comandoFichero]()



# 7.4 Visualizando archivos HTML en terminal

## 7.4.1 Diferencia entre CLI y GUI
- CLI es una interfaz basada en texto donde se ejecutan comandos.
- GUI es una interfaz visual con ventanas y botones.

## 7.4.2 Importancia de la dirección IP 127.0.0.1
Es la dirección de loopback usada para acceder al propio sistema local.

## 7.4.3 Visualización del archivo en Lynx
Ejecutamos lynx 127.0.0.1/test.html

## Visualización
![Visualizacion]()

## 7.4.4 Visualización desde la máquina host
Obtener la IP de la máquina virtual con ifconfig o ip a
Acceder desde un navegador en Windows a http://10.0.2.15/test.html



# 7.5 Creando y visualizando archivos PHP

## 7.5.1 Función de phpinfo();
Muestra información detallada sobre la configuración de PHP y Apache.

## 7.5.2 Visualización del archivo en Lynx
Creamos un archivo nse.php
Ejecutamos lynx 127.0.0.1/nse.php para verlo

## Visualización
![Visualizacion2]()



# 7.6 Explorando y editando el archivo hosts

## 7.6.1 Edición del archivo /etc/hosts
Abrimos /etc/hosts.
Agregamos la línea 127.0.0.1 www.example.com antes de # End of hosts.

## 7.6.2 Verificación de la configuración
Ejecutamos lynx www.example.com