Cada dispositivo de internet  cuenta con una ip publica, al principio se liberaron 32 bits para la asignación de ips b en la estructura

	255.255.255.255

por lo tanto se pueden asignar **4.294.967.296 direcciones únicas** pero la cantidad de dispositivos conectados a internet se incremento drásticamente, es por eso que implementaron varias estrategias para cubrir este agotamiento:

![[Pasted image 20230105104710.png]]

En este apartado la *Traducción de direcciones de red (NAT)*.

Ahora una particularidad de las *ip privadas*, es que no necesitas pagar o pedir permiso para usar estas, al contrario con las *ip publicas* que debes no solo pagar por hacer uso de ellas si no también realizar una solicitud formal con contrato incluido a un *ISP* o un *RIR* dependiendo del tamaño de tu empresa para poder utilizarlas.

![[Pasted image 20230105111135.png]]

*¿De que va NAT?*
Pues bueno esto básicamente se basa en tomar una IP privada y mapearla o traducirla a una dirección publica o viceversa.

*¿Para que utilizar NAT?*
Es utilizada para que nuestros dispositivos en la red configurados con direcciones ip privadas de comuniquen a través de internet, recordando que solo las ip publicas son enrutables a internet, mientras que las ip privadas no.

![[Pasted image 20230105111649.png]]

pero se estarán preguntado *¿Qué sentido tiene hacer uno de NAT, cuando podemos hacer uso de una IP publica directamente?*

1. Agotamiento, Como se comento anteriormente para reducir al agotamiento de las direcciones *IPv4*.
2. Costo, Arrendar una dirección *IPv4* publica no es nada barato.
Es decir que si queremos conectar unos 1000 nodos a internet, debemos contratar un bloque de direcciones que satisfaga esto numero, lo cual tiene su costo algo elevado.
3. Economía, miles de nodos pueden conectarse a internet haciendo uso de una sola ip publica.


## Identificando direcciones IPv4 publicas e IPv4 privadas 
Ahora hablaremos de los bloques de ip, para que podamos identificarlas.

Las direcciones ip publicas disponibles que son *4,294,967,296* se dividen en clases, resultado así las clases *A*, *B*, *C*, *D* y *E*.

Las direcciones asignables a nodos se encuentran en *A*, *B* y *C*. Mientras que las clases *D* y *E* sirven para otros propósitos en redes.

![[Pasted image 20230105113559.png]]

Estos seria los rangos que cubren cada clase de ips publicas:

![[Pasted image 20230105113800.png]]

Pero en estos rango tenemos tanto las direcciones ip publicas e ip privadas, por esto veremos los rangos de las ip privadas en las diferentes clases:

![[Pasted image 20230105113921.png]]

Entonces el trabajo de NAT seria, por ejemplo contar con una ip privada y mapearla o traducirla a una ip publica.

![[Pasted image 20230105114035.png]]







## Tipos de NAT

- Estático
Este funcionamiento le otorga a una ip *privada* de una red una ip *publica* sin ser cambiada.

- Dinámico
Esto consiste en tener una red de dispositivos y el que desee conectarse a internet otorgarle una ip *publica* a cada uno de estos.

- Sobrecargar
Este tipo es el mas común ya que se utiliza en las redes domesticas, ya que resulta mas económico, consiste en que todo la red cuente con ip *privadas* y que estas al salir a internet salgan por una solo ip *publica*, que dependiendo el proveedor de internet esta cambia cada cierto tiempo.

- Solapamiento
Cuando una dirección IP privada de una red es una dirección IP pública en uso, el router se encarga de **reemplazar dicha dirección** IP por otra para evitar el conflicto de direcciones.