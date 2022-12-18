Cada dispositivo de internet  cuenta con una ip publica, al principio se liberaron 32 bits para la asignación de ips en la estructura

	255.255.255.255
por lo tanto se pueden asignar **4.294.967.296 direcciones únicas** pero la cantidad de dispositivos conectados a internet se incremento drásticamente, es por eso que se implemento el protocolo **Network Address Translation**.

El objetivo de este protocolo es otorgar ips *privadas* a una red de dispositivos, para que cuando se desean conectar a internet de les otorgué una ip *publica*.

## Tipos de funcionamiento

- Estático
Este funcionamiento le otorga a una ip *privada* de una red una ip *publica* sin ser cambiada.

- Dinámico
Esto consiste en tener una red de dispositivos y el que desee conectarse a internet otorgarle una ip *publica* a cada uno de estos.

- Sobrecargar
Este tipo es el mas común ya que se utiliza en las redes domesticas, ya que resulta mas económico, consiste en que todo la red cuente con ip *privadas* y que estas al salir a internet salgan por una solo ip *publica*, que dependiendo el proveedor de internet esta cambia cada cierto tiempo.

-Solapamiento
Cuando una dirección IP privada de una red es una dirección IP pública en uso, el router se encarga de **reemplazar dicha dirección** IP por otra para evitar el conflicto de direcciones.