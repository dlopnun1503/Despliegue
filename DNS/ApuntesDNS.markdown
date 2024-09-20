# DNS

## Resolución
La resolución de nombres de dominio permite navegar por Internet utilizando nombres de dominio en lugar de direcciones numéricas.

## Nombre de dominio
Un nombre de dominio es un nombre fácil de recordar asociado a una dirección IP física de Internet.

## Niveles de dominio
Los niveles de dominio se refieren a la jerarquía de nombres de dominio utilizados para identificar y organizar los recursos en Internet.

## Zonas de búsqueda
Se refiere a una porción específica del espacio de nombres de dominio que es administrada por una entidad o servidor DNS. Cada zona contiene información sobre un dominio y sus subdominios, y se gestiona mediante un servidor de nombres autoritativo.

## Tipos de servidores
Existen varios tipos de servidores DNS:
- Recursivo: Recibe consultas del cliente y busca respuestas.
- Autoritativo: Contiene los datos oficiales de un dominio.
- Raíz: Dirige las consultas a los servidores TLD.
- TLD: Maneja información sobre los dominios de nivel superior.
- Caché: Almacena respuestas para acelerar futuras consultas.
- Inverso: Traduce direcciones IP a nombres de dominio.

## Funcionamiento
DNS es el sistema encargado de traducir nombres de dominio legibles por humanos a direcciones IP numéricas, que las máquinas usan para identificar recursos en Internet. En este proceso, pueden ocurrir dos tipos de consultas: recursivas e iterativas.
### Consulta recursiva
En una consulta recursiva, un cliente solicita la resolución de un nombre de dominio a un servidor DNS recursivo, y espera que este servidor se encargue de encontrar la respuesta final, ya sea solicitando la información a otros servidores DNS o proporcionando una respuesta en caché.
### Consulta iterativa
En una consulta iterativa, el cliente le solicita al servidor DNS una respuesta, pero el servidor no se encarga de completar todo el proceso. En lugar de eso, el servidor DNS proporciona la mejor respuesta que tiene. El cliente sigue enviando consultas a diferentes servidores DNS hasta que obtiene la dirección IP final.