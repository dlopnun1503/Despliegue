# 3.1 Creating an executable bash script

## Creamos un script llamado test.sh al que le añadimos 
#!/bin/bash
clear
echo "Hello World"

## Ponemos el script como ejecutable 
chmod +x test.sh

## Lo ejecutamos, una vez ejecutado solo deberíamos ver un mensaje con hello world y el prompt
./test.sh

## NOTA
No debemos usar chmod 777 test.sh ya que otorgaríamos todos los privilegios a todo el mundo, esto no es buena práctica, sobre todo por temas de seguridad.

## Resultado 3.1 -> Vemos como muestra el mensaje del fichero test.sh
![Resultado3.1]()


# 3.2 Creating new users

## Creamos los usuarios
sudo useradd -m bob
sudo useradd -m smith

## Le ponemos la contraseña correcta
passwd bob
passwd smith

## Resultado 3.2
![Resultado3.2]()


# 3.3 Creating a shared executable script

## Creamos el directorio
sudo mkdir /home/ncs

## Cambiamos los permisos para que pueda ser legible y escribible por todos 
sudo chmod 777 /home/ncs

## Nos movemos al directorio que hemos creado
cd /home/ncs

## Creamos el script y le añadimos
#!/bin/bash
echo "HelloWorld"

## Ponemos el script como ejecutable 
chmod +x hello.sh

## Ejecutamos el script
./hello.sh

## Comprobamos los detalles de propiedad y permisos del archivo
ls -l /home/ncs/hello.sh

## Resultado 3.3
![Resultado3.3]()


# 3.4 Accessing files from different user accounts

## PARTE A
En este caso debemos inicar sesión con bob

## En la carpeta cd /home/ncs ejecutamos 
ls -l

## Ejecutamos ./hello.sh
En este caso podemos ver su contenido ya que en el apartado 3.3 le dimos los permisos necesarios para poder ejecutarlo

## Creamos un archivo bob.sh y le añadimos
#!/bin/bash
echo "Hello this is Bob"

## Le damos los permisos de ejecución 
chmod +x bob.sh

## Lo ejecutamos 
./bob.sh

## Resultado 3.4.A -> en esta captura no muestra el prompt  ya que he iniciado sesión con bob
![Resultado3.4.A]()


## PARTE B
En este caso debemos inicar sesión con smith

## En la carpeta cd /home/ncs ejecutamos 
ls -l

## Ejecutamos ./hello.sh y ./bob.sh
En este caso tendremos permisos para ejecutar el hello.sh pero no bob.sh ya que bob es el propietario del archivo y no se han dado los permisos necesarios.


