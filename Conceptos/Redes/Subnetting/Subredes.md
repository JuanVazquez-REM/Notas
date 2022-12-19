Conocimientos previos:
- [[NAT]]

## ¿Qué es el subnetting ?
Es una técnica para dividir una red de Ip's físicas en varias redes lógicas pequeñas. La técnica que se explicara a continuación es la tradicional, ya que esta se basa en crear subredes con igualdad de hosts en todas estas, dejando en algunas ocasiones ips sin utilizar, existe otro técnica de subnetting llamada [[VLSM]], pero te primero te recomiendo que aprendas esta técnica.

Empecemos, una dirección de red siempre se representa con la porción del host en "cero":

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