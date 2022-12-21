Conocimientos previos:
- [[VLSM]]

Es el proceso de resumir un grupo de redes subneteadas continuas en una sola red grande. También se conoce como resumen de rutas y agregación de rutas.

Supernetting es el proceso contrario al subnetting y consiste en la combinación de varias redes o subredes, tras lo que disminuyen las partes de las direcciones para facilitar mas hosts en una misma red.


## Ejercicio de ejemplo VLSM

Teniendo en cuenta que realizamos un VLSM en una red.

*Dirección Ip*: 192.168.10.10/26
*Hosts solicitados:*
- 50 hosts
- 20 hosts
- 10 hosts
- 10 hosts

Omitiendo toda la aplicación del esquema VLSM en esta red, tendremos como resultado las siguientes subredes.

| N°  | Hosts Solicitados | Hosts Encontrado | Dirección de Red | Prefijo | Mascara Decimal Punteada | Primera IP Utilizable | Ultima IP Utilizable | Dirección de Broadcast |
| --- | ----------------- | ---------------- | ---------------- | ------- | ------------------------ | --------------------- | -------------------- | ---------------------- |
| 1   | 50               | 62              | 192.168.10.0      | /26     | 255.255.255.192          | 129.168.10.1           | 192.168.10.62        | 192.168.10.63          |
| 2   | 20                | 30               | 192.168.10.64    | /27     | 255.255.255.224          | 129.168.1.65         | 192.168.10.94        | 192.168.10.95          |
| 3   | 10                | 14               | 192.168.10.96    | /28     | 255.255.255.240          | 192.168.1.97         | 192.168.10.110        | 192.168.10.111          |
| 4   | 10                | 14               | 192.168.1.112    | /28     | 255.255.255.240          | 192.168.1.113         | 192.168.10.126        |   192.168.10.127                     |

Con un esquema similar al siguiente.

![[Pasted image 20221219114537.png]]

Ahora observando este diagrama nos quedarían 4 subredes,  totalmente aisladas, *a menos que el router sea de capa 3, esto interconectara la subredes haciendo visible cada una de estas para las demás subredes*.

Para tener comunicación entre estas se puede utilizar el concepto de *Supernetting*, esta direcciona una cantidad de subredes IP utilizando una única ruta. *A esta ruta se le suele denominar ruta sumarizada o supernet*.

## Sumarizacion

Lo que se pretende hacer es unir subredes subiendo el numero mascara de subred.

Quiero unir las siguientes rutas:

- 192.168.10.0
- 192.168.11.0
- 192.168.12.0
- 192.168.13.0

Son redes totalmente aisladas, para esto aplicaremos el Supernetting.

Primero debes de pasar estas direcciones Ip a bits, quedándonos de la siguiente manera.

- 192.168.10.0  =  <mark style="background: #FF5582A6;">11000000  10101000  00001</mark>010  00000000
- 192.168.11.0  =   <mark style="background: #FF5582A6;">11000000  10101000  00001</mark>011  00000000
- 192.168.12.0 =    <mark style="background: #FF5582A6;">11000000  10101000  00001</mark>100  00000000
- 192.168.13.0 =     <mark style="background: #FF5582A6;">11000000  10101000  00001</mark>001  00000000
---
Resultado =   11000000  10101000  00001000  00000000 
Dirección Ip  = *192.168.8.0/21 255.255.248.0*

Y marcamos los bits que coinciden con las demás subredes, la ip resultante de esto será una nueva red.

| Subnet address | Host address range          | Broadcast address |
| -------------- | --------------------------- | ----------------- |
| 192.168.8.0    | 192.168.8.1 - 192.168.15.254 | 192.168.15.255     | 

Ahora vamos con un ejercicio en Packet Tracer, donde representaremos las subredes hechas anteriormente con VLSM, y veremos que a cada red se les asigno a una computadora la primera ip disponible de esa red.

![[Pasted image 20221219122031.png]]

Al hacer ping a otra red, esta nunca responderá, por que están en diferente red.

![[Pasted image 20221219122451.png]]

Pero si colocamos la mascara de subred obtenida por la sumatoria de las subredes en la maquinas, es decir la *255.255.248.0* esta será posible la comunicación a pesar de ser redes diferentes.

![[Pasted image 20221219122634.png]]

Esto sucede ya que la mascara de red perteneciente a la dirección Ip *192.168.8.0/21* abarca muchos mas hosts, ya que su rango seria de *192.168.8.1 - 192.168.15.254* como se mostro en la anterior tabla en respuesta de la sumatoria de subredes. 

![[Pasted image 20221219122837.png]]

Las demás computadoras con mascara *255.255.255.0* no responderán al ping a menos de que esta sea cambiada por la mascara de red de la supernet.

Esto es todo.