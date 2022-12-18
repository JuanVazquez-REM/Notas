Las tramas 802.11 de gestión son las que permiten mantener comunicaciones a las estaciones inalámbricas y tenemos distintos tipos.

Existen diferentes tramas de gestión en este caso solo veremos las siguientes:

1. Beacon frames
2. Probe Request
3. Probe Response

### Beacon Frames
Esta trama lo que hace es difundir la presencia del access point y la configuración básica del access point a las estaciones cliente en su radio de cobertura.

Las estaciones pueden obtener litas de access point disponibles buscando tramas Beacon continuamente.

Las tramas beacon contienen la informacion necesaria para identificar las características de la red y poder conectarnos al access point deseado.

Entonces los routers van a estar emitiendo tramas beacon continuamente para nosotros.

### Probe Request
Esta trama lo que hace es emitir tramas de todas nuestras redes wifi guardadas en nuestro dispositivo, cuando se encuentra una red cerca de nuestra área el router nos emitirá una trama probe response entonces nos podemos conectar de forma automática a nuestra red wifi.

Por esta razón nuestros dispositivos se conectan a una red de forma automática cuando ya no hemos conectado anteriormente a la red.

### Probe Response
Esta trama como se vio anteriormente es la respuesta del router al recibir una trama probe request.

### Association Request
Esto sucede cuando el dispositivo manda un *Probe Request* y el AP le contesta con un *Probe Response*, a continuación el dispositivo manda un paquete *association request*, en espera de una respuesta.

### Association Response
Este paquete se da a la respuesta del *association request*.

### Authentication 
Este paquete se emite cuando se realiza una asociación

### DeAuthentication
Este paquete se envia cuando se desea desconectar del AP

### Dissasociation Frame
Esto pasa cuando se emite cuando ocurre una DeAuthentication. 

