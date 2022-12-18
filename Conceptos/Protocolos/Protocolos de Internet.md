
## Protocolos

### TCP / IP
Es un conjunto de reglas estandarizadas que permiten a los equipos comunicarse en una red como Internet.

**TCP** e **IP** son dos protocolos distintos para redes informáticas.

**IP** es la parte que obtiene la dirección a la que se envían los datos. **TCP** se encarga de la entrega de los datos una vez hallada dicha [dirección IP](https://www.avast.com/es-es/c-what-is-an-ip-address).


### UDP
El protocolo de [[Datagramas]] de usuario, abreviado como UDP, es un protocolo **que permite la transmisión sin conexión de datagramas** en redes basadas en IP. 

El protocolo TCP tiene lugar una vez se ha producido el enlace obligatorio de 3 vías (con acuse de recibo mutuo entre el emisor y el receptor, incluida la sesión de comunicación), el protocolo UDP no utiliza este procedimiento con el fin de mantener el **tiempo de transmisión** lo más bajo posible.

Se utiliza para **transmitir datagramas de forma rápida en redes IP** y funciona como una alternativa sencilla y sin retardos del protocolo TCP. Se usa principalmente para consultas DNS, conexiones VPN y para el streaming de audio y vídeo.


## Tipos de paquetes

### SYN
Este paquete se envía cuando el cliente desea establecer una conexión, manda un paquete SYN (snychronize) con un numero de secuencia individual o aleatorio. Este numero garantiza la transmisión completamente en orden, sin *duplicados*, por si todo esta correcto consecuencia crea una sesion para su comunicacion.

Se usa para **sincronizar los números de secuencia en tres tipos de segmentos: petición de conexión, confirmación de conexión (con ACK activo) y la recepción de la confirmación (con ACK activo)**.


## Modos

### NAT
Es el modo de conexion mas facil para que una MV tenga conexion a internet.
Funciona de la siguiente manera, VM coloca un router DHCP entre la conexión externa (Internet) y las MV's, dicho router asigna ip's a partir de una subred.
Por lo tanto la subred esta aislada de la red física.

Nota: Existe conexión por parte del host NAT.

### Briged
Este modo simula que la tarjeta de red virtual esta conectada a la red, por lo tanto la maquina virtual se hace pasar por una maquina física, por lo tanto puede interactuar con las demás maquinas.


