#  Beacon Flood Mode Attack
Consiste en generar muchos acces point en un canal espesifico para que el canal se sature y los AC expulsen a sus dispositivos conectados.

	mdk3 wlan1mon b -f nombre.txt -a -s 1800 -c 6
Lo que hace es generar con los nombres que ingrese en el txt generar AC en el canal 6

- b *indicamos a mdk3 que se realizara un ataque BFMA*
-  f *se espesifica el nombre que tendran los AC y junto a esto anexamos el archivo* (Esto se puede omitir y mdk3 generar AC con nombre random continuamente)
-  a *especificamos que vamos a crear AC con cifrado AES*
-  s *para la cantidad de paquetes por segundo es 1800 paquetes*
-   c *especificamos el canal donde de crean los AC*
-