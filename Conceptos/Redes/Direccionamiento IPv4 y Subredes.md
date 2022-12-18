Empecemos con lo primordial que es un dirección IPv4.

> Una dirección IP es un numero binario de 32 Bits, esta es compuesta por un identificador de RED y un identificador de HOST
> 
> [[Tema 2 Transmision de datos#El bit|Mas informacion sobre los bits.]]

![[Pasted image 20221217194751.png]]

Cada octeto representa un Byte. 
El valor máximo de un Byte es de 2^8=256
El valor decimal máximo para cada byte en decimal es de *255*


## Identificador de RED y HOST

En 1981, las direcciones IPv4 de internet se asignaban mediante la direccionamiento con clase, a los clientes se les asigno un dirección de red basada en una de las tres clase: A, B, o C que son las denominadas clase antigua.

Esta clase quedo obsoleta al emerger nuevas tecnologías, sin embargo sigue en usa en muchas plataformas actuales.

La cantidad de bits asignados al identificador de red y host, *dependen directamente de la clase a la que pertenezca una dirección ip dada*. 


## Clases de direcciones IPv4

Existen cinco clase de direcciones IP:

| Clase | Característica                     |
|:-----:| ---------------------------------- |
|   A   | Soporta redes en internet grandes  |
|   B   | Soporta redes en internet modernas |
|   C   | Soporta redes en internet pequeñas |
|   D   | Soporta redes multicast            |
|   E   | Sin uso. Redes experimentales      |

La direcciones IP de clase **A** reservan el primer Byte para la asignación del identificador de red.
![[Pasted image 20221217201913.png]]

La direcciones IP de clase **B** reservan el primer y segundo Byte para la asignación del identificador de red.
![[Pasted image 20221217201938.png]]

La direcciones IP de clase **C** reservan el primer, segundo y tercer Byte para la asignación del identificador de red.
![[Pasted image 20221217202025.png]]

**¿Cómo se determina la clase de una IP?**
La respuesta a esto esta en el primer Byte.

| Clase | Característica                                  |
|:-----:| ----------------------------------------------- |
|   A   | El primer byte esta comprendido entre 0 - 127   |
|   B   | El primer byte esta comprendido entre 128 - 191 |
|   C   | El primer byte esta comprendido entre 192 - 223 |
|   D   | El primer byte esta comprendido entre 224 - 239 |
|   E   | El primer byte esta comprendido entre 240 - 255 |

Ejemplo de direcciones de *clase A*

- 10.24.124.67
- 127.32.120.12
- 77.24.34.253.193

Ejemplo de direcciones de *clase B*

- 128.124.12.53
- 154.91.110.34
- 191.191.43.13

Ejemplo de direcciones de *clase C*

- 192.168.1.72
- 223.81.33.4
- 210.132.52.235

## En resumen

Dada una dirección *clase A* el primer Byte es el identificador de red y lo restante el identificador del host.

![[Pasted image 20221217203540.png]]


Dada una dirección *clase B* el primer Byte es el identificador de RED y lo restante el identificador del HOST.

![[Pasted image 20221217203556.png]]

Dada una dirección *clase C* el primer Byte es el identificador de red y lo restante el identificador del host.

![[Pasted image 20221217203631.png]]


## Mascaras y prefijos 

La mascara de RED/SUBRED es un numero en notación decimal punteada, que opera en un conjunto con una dirección IP. Su propósito es identificar "*Explícitamente*" los bits de la porción de red y los bits de la porción del host de la dirección IP.

La porción de red representa con unos (1) binario y la porción de host con ceros (0) binario.

**Ejemplo**

![[Pasted image 20221217210118.png]]

La *mascara de red* indica "Explícitamente" cuantos bits de red y cuantos bits de host tiene la dirección IP sobre la que opera.

También podemos utilizar una notación de prefijo de red, de manera mucho mas simple, indicando solo la cantidad en bits de red.

192.168.168/24 ->/24 *Prefijo de red (clase C)*
172.16.10.15/16 -> /16 *Prefijo de red (clase B)*
10.3.2.12/8 -> /8 *Prefijo de red (clase A)*


# Subredes

Una dirección de red siempre se representa con la porción del host en "cero":

	192.168.1.0

Dentro de esta red se pueden direccionar 254 hosts. La porción de host esta compuesta por ocho bits, por lo tanto: *2^8 = 256-2 = 254*.

	192.168.1.1
	192.168.1.2
	192.168.1.3
	.                                  
	.
	.
	192.168.1.254

*0* Es la propia dirección de red y *255* es la dirección de difusión.

## ¿Cómo dividir la red en subredes?

La división en subredes permite administrar mas eficientemente las direcciones IP. Este método consiste en dividir las clases de direcciones de red completas en partes de menos tamaño.

Para hacer esto, se pide *prestados bits de la porción de host* para asignarlos a la porción de red. Los bits de host se deben de reasignar como bits de subred. *El punto de inicio de este proceso se encuentra siempre den el bit del host del extremo izquierdo*, aquel que se encuentra mas cerca del byte de red anterior.

**Ejemplo 1:**
Dirección de la red = 192.168.168.0
Cantidad de subredes solicitadas = 8

Inspeccionando el primer byte de la dirección de red podemos saber que es una *ip de clase C*
Por lo tanto la mascara de red:

	255.255.255.0 //decimal
	11111111.11111111.1111111.0000000 //binario

Entonces, vamos a tomar la cantidad de bits necesaria del host, para la creacion de las ocho subredes.

Para llegar a esto debemos de *tomar prestado la cantidad de bits que elevados a la 2 nos de como resultado la cantidad de las subredes solicitadas* (No importa si este la cantidad de subredes sobre pasa las solicitadas).

Para este caso la cantidad serán 3 bits ya que si hacemos los cálculos nos dará 8.
![[Pasted image 20221217232521.png]]

Ahora el valor de los los bits a decimal nos debe de dar la *mascara de red*.

![[Pasted image 20221217233543.png]]

Para saber el rango de las subredes podemos dividir las subredes entre 256 (valor máximo de un byte a decimal) 

	subredes/valor_maximo_de_un_byte = rango
	8/256 = 32

Por lo tanto tanto las subredes serias las siguientes:

192.168.168.0 -> subred *1*
192.168.168.32 -> subred *2*
192.168.168.64 -> subred *3*
192.168.168.96 -> subred *4*
192.168.168.128 -> subred *5*
192.168.168.160 -> subred *6*
192.168.168.192 -> subred *7*
192.168.168.224 -> subred *8*

El broadcast es un valor menos que la mascara de red, es decir:

Dirección de red = 192.168.168 *&* 192.168.168.32 *&* 129.168.168.64
Broadcast            = 192.168.168.31 *&* 192.168.63 *&* 192.168.168.95


**Ejemplo 2:** 
Dirección de la red = 192.168.1.0
Cantidad de subredes solicitadas = 3

![[Pasted image 20221217235706.png]]

	subredes/valor_maximo_de_un_byte = rango
	4/256 = 64

Por lo tanto tanto las subredes serias las siguientes:

192.168.1.0 -> subred *1*
192.168.1.64 -> subred *2*
192.168.1.128 -> subred *3*
192.168.1.192 -> subred *4*

El broadcast es un valor menos que la mascara de red, es decir:

Dirección de red = 192.168.1.0 *&* 192.168.1.64 *&* 129.168.1.128 *&* 192.168.1.192
Broadcast            = 192.168.1.63 *&* 192.168.1.127 *&* 192.168.1.191 *&* 192.168.1.255