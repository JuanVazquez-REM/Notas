Conocimientos previos:
- [[Direccionamiento IPv4]]
- [[Subredes]]

Mascaras de subred de longitud es una técnica creada para evitar el agotamiento de direcciones IPv4.

## Esquema Tradicional
Como bien sabemos con el esquema tradicional de subredes podíamos *dividir la red en subredes teniendo una igualdad de host disponibles en cada subred*, tal y como se muestra en la ilustración:

![[Pasted image 20221218165636.png]]

En este ejemplo se puede visualizar que existen *8 subredes, 4 redes LAN y 4 redes WAN*, las cuales cada una de estas subredes tiene como ip disponibles 30.

Las redes WAN solo se utiliza 2 ips por cada una de estas, esto nos deja con muchas direcciones ip sin usar.

## Implementación VLSM
Esta técnica a comparación del esquema de direccionamiento tradicional esta se divide en las direcciones que son requeridas y no en la cantidad de subredes crear.

### Ejemplo 1

Dirección Ip: 192.168.1.0/24
Hosts solicitados: 60 hosts, 120 hosts 10, hosts 24 hosts.

Para llevar un control de las redes que se irán creando estableceros una tabla con informacion de cada una de las redes, sale?

| N°  | Hosts Solicitados | Hosts Encontrado | Dirección de Red | Prefijo | Mascara Decimal Punteada | Primera IP Utilizable | Ultima IP Utilizable | Dirección de Broadcast |
| --- | ----------------- | ---------------- | ---------------- | ------- | ------------------------ | --------------------- | -------------------- | ---------------------- |
| 1   |       120            |                  |                  |         |                          |                       |                      |                        |
| 2   |        60         |                  |                  |         |                          |                       |                      |                        |
| 3   |        24         |                  |                  |         |                          |                       |                      |                        |
| 4    |         10        |                  |                  |         |                          |                       |                      |                        |

#### Subred N°1

<mark style="background: #BBFABBA6;">Paso 1:</mark> Ordenar los hosts solicitados del mayor al menor, ya que empezaremos con el numero mayor de hosts solicitados.

	120 host, 60 hosts, 24 hosts, 10 hosts

<mark style="background: #BBFABBA6;">Paso 2:</mark> Identificar la mascara de red actual, es decir la mascara de 192.168.1.0/24, con el sufijo podemos determinar que la mascara en bits tendrá 24 bits como unos mientras que los sobrantes en ceros.

![[Pasted image 20221218171021.png]]

Mascara de red actual : *255.255.255.0*

<mark style="background: #BBFABBA6;">Paso 3:</mark> Aplicar la formula, para calcular la cantidad de hosts de cada subred.

	hostsDisponibles = 2^n - 2 >= cantidad_hosts

Empezando por el primer hosts a calcular seria *120*, en base a la siguiente que elevación a la 2 como resultado es igual mayor a la cantidad de hosts solicitados.

| 2^7   | 2^6   | 2^5   | 2^4   | 2^3   | 2^2   | 2^1   | 2^0   |
| --- | --- | --- | --- | --- | --- | --- | --- |
| 128 | 64  | 32  | 16  | 8   | 4   | 2   | 1   | 

En este caso seria la elevación de *7* ya que su resultado es mayor a la cantidad de hosts solicitados. Entonces aplicamos la formula:

	2^7 - 2 >= 120 
	128 -2 >= 120
	126 >= 120 //TRUE

Esto nos da como resultado *126 hosts disponibles* para la *primera solicitud de 120 hosts*.

> Nota
> En el mayoría de los cálculos no tendremos los hosts disponibles exactamente que los solicitados, pero esto nos deja con la posibilidad de agregar un par de hosts mas posteriormente.

<mark style="background: #BBFABBA6;">Paso 4:</mark> Obtener la nueva mascara de subred.

Para calcular la nueva mascara tendremos que recordar la mascara actual y el numero de elevaciones (*7*) para sacar los hosts disponibles de la primera red.

	MascaraDeRedActual = 11111111.11111111.11111111.00000000
	MascaraDeRedActual_Decimal = 255.255.255.0

Ahora con la elevación de *7*, indicara el numero de bits apagados en el ultimo octeto, es decir que solo estará un bit encendido.

	NuevaMascaraDeRed = 11111111.11111111.11111111.10000000
	NuevaMascaraDeRed_Decimal = 255.255.255.128
	Prefijo = /25

<mark style="background: #BBFABBA6;">Paso 5:</mark> Calcular el salto de red. Esto nos indica donde empezara la siguiente dirección de red (como esta es la primera red, nuestra dirección de red empieza en la 192.168.1.0).

Esto se calcula con la constate de 256.

	256 - 128 (Valor del ultimo octeto de la nueva mascara de red (128))
	= 128

Con esto datos ya tendríamos la primera subred, vamos a llenar la tabla.

| N°  | Hosts Solicitados | Hosts Encontrado | Dirección de Red | Prefijo | Mascara Decimal Punteada | Primera IP Utilizable | Ultima IP Utilizable | Dirección de Broadcast |
| --- | ----------------- | ---------------- | ---------------- | ------- | ------------------------ | --------------------- | -------------------- | ---------------------- |
| 1   | 120               | 126              | 192.168.1.0      | /25     | 255.255.255.128          | 129.168.1.1         | 192.168.1.126        |    192.168.1.127                    |
| 2   | 60                |                  | 129.168.1.128    |         |                          |                       |                      |                        |
| 3   | 24                |                  |                  |         |                          |                       |                      |                        |
| 4   | 10                |                  |                  |         |                          |                       |                      |                        |

##### Orientación del llenado de la tabla

- **Mascara Decimal Punteada**
Sera la nueva mascara de la subred obtenida, cada subred tendrá so propia mascara.

- **Dirección de red**
Donde empieza la subred, nuestra primera subred empieza en 192.168.1.0, es por eso que intuimos que la segunda red empezara donde termina la primera mas uno, es decir 192.168.1.128.

- **Primera IP Utilizable**
Sera la dirección de red de la propia subred mas uno, es decir 192.168.1.1

- **Dirección de Broadcast**
Sera un numero menos que la nueva mascara de red, es decir 192.168.1.127

- **Ultima  IP Utilizable**
Sera la dirección broadcast menos uno, es decir 192.168.1.126.

*En este punto ya tendremos la primera subred.*

#### Subred N°2

Ahora para calcular la siguiente subred, realizaremos los mismos pasos que los anteriores.

<mark style="background: #BBFABBA6;">Paso 1:</mark> Identificar con que hosts trabajaremos (mayor a menor).

	120 host, 60 hosts, 24 hosts, 10 hosts

*60 hosts*

<mark style="background: #BBFABBA6;">Paso 2:</mark> Identificar la mascara actual.
Repetiremos todos los pasos menos este ya que siempre se trabajara con la mascara de red actual, nunca con una mascara nueva o generada. *Así que el paso 2 esta hecho, solo repetiré la misma informacion*.

![[Pasted image 20221218171021.png]]

	MascaraDeRedActual_Decimal = 255.255.255.0

> Nota
> No debes e usar la nueva mascara obtenida de la primer subred, debes de usar la mascara de la red actual, sale?


<mark style="background: #BBFABBA6;">Paso 3:</mark> Aplicar la formula, omite la explicación, ya que esto ya se explico en la primera subred  realizada.

	hostsDisponibles = 2^n - 2 >= cantidad_hosts

Tabla de binario a decimal.

| 2^7   | 2^6   | 2^5   | 2^4   | 2^3   | 2^2   | 2^1   | 2^0   |
| --- | --- | --- | --- | --- | --- | --- | --- |
| 128 | 64  | 32  | 16  | 8   | 4   | 2   | 1   | 

Hosts solicitados = 60

En este caso seria la elevación de *6* ya que su resultado es mayor a la cantidad de hosts solicitados. Entonces aplicamos la formula:

	2^6 - 2 >= 60 
	64 - 2 >= 60
	62 >= 60 //TRUE

Hosts encontrado/disponibles = 62.

<mark style="background: #BBFABBA6;">Paso 4:</mark> Obtener la nueva mascara de subred.
Numero de elevaciones (*6*) para sacar los hosts disponibles de la primera red.

	MascaraDeRedActual = 11111111.11111111.11111111.00000000
	MascaraDeRedActual_Decimal = 255.255.255.0

Ahora con la elevación de *6*, indicara el numero de bits apagados en el ultimo octeto.

	NuevaMascaraDeRed = 11111111.11111111.11111111.11000000
	NuevaMascaraDeRed_Decimal = 255.255.255.192
	Prefijo = /26

<mark style="background: #BBFABBA6;">Paso 5:</mark> Calcular el salto de red. Esto nos indica donde empezara la siguiente dirección de red (como esta es la segunda red, nuestra dirección de red empieza donde la primera termina, es decir 192.168.1.128).

Esto se calcula con la constate de 256.

	256 - 192 (Valor del ultimo octeto de la nueva mascara de red (192))
	= 64

Ahora procederemos a agregarla a la tabla, [[VLSM#Orientación del llenado de la tabla|informacion sobre el llenado]].

| N°  | Hosts Solicitados | Hosts Encontrado | Dirección de Red | Prefijo | Mascara Decimal Punteada | Primera IP Utilizable | Ultima IP Utilizable | Dirección de Broadcast |
| --- | ----------------- | ---------------- | ---------------- | ------- | ------------------------ | --------------------- | -------------------- | ---------------------- |
| 1   | 120               | 126              | 192.168.1.0      | /25     | 255.255.255.128          | 129.168.1.1         | 192.168.1.126        |   192.168.1.127                     |
| 2   | 60                | 62               | 192.168.1.128    | /26     | 255.255.255.192          | 129.168.1.129         | 192.168.1.190        | 192.168.1.191          |
| 3   | 24                |                  | 192.168.1.192    |         |                          |                       |                      |                        |
| 4   | 10                |                  |                  |         |                          |                       |                      |                        |

Listo.

#### Subred N°3

<mark style="background: #BBFABBA6;">Paso 1:</mark> Identificar con que hosts trabajaremos (mayor a menor).

	120 host, 60 hosts, 24 hosts, 10 hosts

*24 hosts*

<mark style="background: #BBFABBA6;">Paso 2:</mark> Identificar la mascara actual.


![[Pasted image 20221218171021.png]]

	MascaraDeRedActual_Decimal = 255.255.255.0


<mark style="background: #BBFABBA6;">Paso 3:</mark> Aplicar la formula.

	hostsDisponibles = 2^n - 2 >= cantidad_hosts

Tabla de binario a decimal.

| 2^7   | 2^6   | 2^5   | 2^4   | 2^3   | 2^2   | 2^1   | 2^0   |
| --- | --- | --- | --- | --- | --- | --- | --- |
| 128 | 64  | 32  | 16  | 8   | 4   | 2   | 1   | 

*Hosts solicitados = 24*

En este caso seria la elevación de *5* ya que su resultado es mayor a la cantidad de hosts solicitados. Entonces aplicamos la formula:

	2^5 - 2 >= 24 
	32 - 2 >= 24
	30 >= 24 //TRUE

*Hosts encontrado/disponibles = 30.*

<mark style="background: #BBFABBA6;">Paso 4:</mark> Obtener la nueva mascara de subred.
Numero de elevaciones (*5*) para sacar los hosts disponibles de la primera red.

	MascaraDeRedActual = 11111111.11111111.11111111.00000000
	MascaraDeRedActual_Decimal = 255.255.255.0

Ahora con la elevación de *5*, indicara el numero de bits apagados en el ultimo octeto.

	NuevaMascaraDeRed = 11111111.11111111.11111111.11100000
	NuevaMascaraDeRed_Decimal = 255.255.255.224

*Prefijo = /27*

<mark style="background: #BBFABBA6;">Paso 5:</mark> Calcular el salto de red. Esto nos indica donde empezara la siguiente dirección de red (como esta es la tercera red, nuestra dirección de red empieza donde la segunda termina, es decir 192.168.1.192).

Esto se calcula con la constate de 256.

	256 - 224 (Valor del ultimo octeto de la nueva mascara de red (224))
	= 32

Ahora procederemos a agregarla a la tabla, [[VLSM#Orientación del llenado de la tabla|informacion sobre el llenado]].

| N°  | Hosts Solicitados | Hosts Encontrado | Dirección de Red | Prefijo | Mascara Decimal Punteada | Primera IP Utilizable | Ultima IP Utilizable | Dirección de Broadcast |
| --- | ----------------- | ---------------- | ---------------- | ------- | ------------------------ | --------------------- | -------------------- | ---------------------- |
| 1   | 120               | 126              | 192.168.1.0      | /25     | 255.255.255.128          | 129.168.1.1           | 192.168.1.126        | 192.168.1.127          |
| 2   | 60                | 62               | 192.168.1.128    | /26     | 255.255.255.192          | 129.168.1.129         | 192.168.1.190        | 192.168.1.191          |
| 3   | 24                | 30               | 192.168.1.192    | /27     | 255.255.255.224          | 192.168.1.193         | 192.168.1.222                     | 192.168.1.223          |
| 4   | 10                |                  | 192.168.1.224                 |         |                          |                       |                      |                        |

Listo.


#### Subred N°4

<mark style="background: #BBFABBA6;">Paso 1:</mark> Identificar con que hosts trabajaremos (mayor a menor).

	120 host, 60 hosts, 24 hosts, 10 hosts

*10 hosts*

<mark style="background: #BBFABBA6;">Paso 2:</mark> Identificar la mascara actual.


![[Pasted image 20221218171021.png]]

	MascaraDeRedActual_Decimal = 255.255.255.0


<mark style="background: #BBFABBA6;">Paso 3:</mark> Aplicar la formula.

	hostsDisponibles = 2^n - 2 >= cantidad_hosts

Tabla de binario a decimal.

| 2^7   | 2^6   | 2^5   | 2^4   | 2^3   | 2^2   | 2^1   | 2^0   |
| --- | --- | --- | --- | --- | --- | --- | --- |
| 128 | 64  | 32  | 16  | 8   | 4   | 2   | 1   | 

*Hosts solicitados = 10*

En este caso seria la elevación de *4* ya que su resultado es mayor a la cantidad de hosts solicitados. Entonces aplicamos la formula:

	2^4 - 2 >= 10 
	16 - 2 >= 10
	14 >= 10 //TRUE

*Hosts encontrado/disponibles = 14*

<mark style="background: #BBFABBA6;">Paso 4:</mark> Obtener la nueva mascara de subred.
Numero de elevaciones (*4*) para sacar los hosts disponibles de la primera red.

	MascaraDeRedActual = 11111111.11111111.11111111.00000000
	MascaraDeRedActual_Decimal = 255.255.255.0

Ahora con la elevación de *4*, indicara el numero de bits apagados en el ultimo octeto.

	NuevaMascaraDeRed = 11111111.11111111.11111111.11110000
	NuevaMascaraDeRed_Decimal = 255.255.255.240

*Prefijo = /28*

<mark style="background: #BBFABBA6;">Paso 5:</mark> Calcular el salto de red. Esto nos indica donde empezara la siguiente dirección de red (como esta es la cuarta red, nuestra dirección de red empieza donde la tercera termina, es decir 192.168.1.224).

Esto se calcula con la constate de 256.

	256 - 240 (Valor del ultimo octeto de la nueva mascara de red (240))
	= 16

Ahora procederemos a agregarla a la tabla, [[VLSM#Orientación del llenado de la tabla|informacion sobre el llenado]].

| N°  | Hosts Solicitados | Hosts Encontrado | Dirección de Red | Prefijo | Mascara Decimal Punteada | Primera IP Utilizable | Ultima IP Utilizable | Dirección de Broadcast |
| --- | ----------------- | ---------------- | ---------------- | ------- | ------------------------ | --------------------- | -------------------- | ---------------------- |
| 1   | 120               | 126              | 192.168.1.0      | /25     | 255.255.255.128          | 129.168.1.1           | 192.168.1.126        | 192.168.1.127          |
| 2   | 60                | 62               | 192.168.1.128    | /26     | 255.255.255.192          | 129.168.1.129         | 192.168.1.190        | 192.168.1.191          |
| 3   | 24                | 30               | 192.168.1.192    | /27     | 255.255.255.224          | 192.168.1.193         | 192.168.1.222        | 192.168.1.223          |
| 4   | 10                | 14               | 192.168.1.224    | /28     | 255.255.255.240          | 192.168.1.225         | 192.168.1.238        |   192.168.1.239                     |

Listo. Este el subnetting con VLSM, lo que quiere decir que cada subred tiene su puerta de enlace (*Dirección de Red*) tiene una mascara de red perteneciente a esa subred, así se aprovecha mejor la red a comparación del subnetting tradicional.