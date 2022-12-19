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


