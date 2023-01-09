Sabemos que internet es una red de redes, Esta esta dividida en cientos de miles de redes pequeñas conocidas como *sistemas autónomos (AS)*. Cada una de etas redes es básicamente una gran conjunto de enrutadores gestionados por una única organización.

![[Pasted image 20230106105053.png]]

Imaginemos que un *AS* como la oficina de correos de una cuidad. El correo va de una oficina de correos a otra hasta que llega a la cuidad correcta, y la oficina de correos de esa cuidad entregara el correo en esa cuidad. Del mismo modo, los paquetes de datos recorren internet saltado de *AS* a *AS* hasta que llegan al *AS* que contiene su dirección de [[Protocolos de Internet # TCP IP|Protocolo de internet (IP)]] de destino. Los entradores dentro de ese *AS* envían paquete a la *dirección IP*.

*Cada AS controla un conjunto especifico de direcciones IP*, al igual que la oficina de correos de cada cuidad es responsable de entregar el correo a todas las direcciones de la cuidad. El rango de *direcciones IP* que controla un determinado *EA* se denomina su "espacio de direcciones IP".

La mayoría de los *AS* se conectan con otros *AS*. Si un *AS* se conecta solo a otro *AS* y comparte la misma política de enrutamiento, se puede considerar una subred del primer *AS*.