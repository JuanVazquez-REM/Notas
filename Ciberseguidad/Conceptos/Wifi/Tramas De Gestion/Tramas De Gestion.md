# Tramas de Gestion
Las tramas 802.11 de gestión son las que permiten mantener comunicaciones a las estaciones inalámbricas y tenemos distintos tipos.

Existen diferentes tramas de gestion en este caso solo veremos las siguientes:

1. Beacon frames
2. Probe Request
3. Probe Response

### Beacon Frames
Esta trama lo que hace es difundir la presencia del access point y la configuracion basica del access poit a las estaciones cliente en su radio de cobertura.

Las estaciones pueden obtener litas de access point disponibles buscando tramas beacon continuamente.
	
Las tramas beacon contienen la informacion nesesaria para identificar las caracteristicas de la red y poder conectarnos al access point deseado.
	
Entonces los routers van a estar emitiendo tramas beacon continuamente para nosotros.

### Probe Resquest
Esta trama lo que hace es emitir tramas de todas nuestras redes wifi guardadas en nuestro dispositivo, cuando se encuentra una red cerca de nuestra area el router nos emitira una trama probe response entonces nos podemos conectar de forma automatica a nuestra red wifi.
	
Por esta razon nuestros dispositivos se conectan a una red de forma automatica cuando ya no hemos conectado anteriormente a la red.

### Probe Response
Esta trama como se vio anteriormente es la respuesta del router al resivir una trama probe resquest.