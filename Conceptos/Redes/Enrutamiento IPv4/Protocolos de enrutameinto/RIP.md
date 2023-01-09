Como hemos visto anteriormente existen protocolos de enrutamiento que nos ayudan en ciertas funciones como:

1. Aprender rutas
2. Elegir la mejor ruta basado en la métrica
3. Converger ante los cambios

Ahora este protocolo pertenece a los *IGPs*, es decir que este trabaja a nivel interno, como se vio en [[10. Diferencias entre IGP y EGP|Diferencias entre IGP y EGP]].

## Funcionamiento

Bien *RIP* es un protocolo de vector de distancia, que utiliza la cantidad de saltos como su métrica principal, dicho esto *RIP* utiliza este algoritmo de vector de distancia para decidir cuales serán las mejores rutas para llegar a un destino.

Cada router *RIP* mantiene una tabla de routing, esta es compartida cada 30 segundos por routers a sus routers vecinos en caso de presentar un cambio en la topología, ah esto se le llama convergencia.

Por ejemplo si un router actualiza una ruta y esta nueva ruta es mas corta, actualizara la tabla de routing. si la nueva ruta es mas larga, esperara un periodo de retención para ver si las actualizaciones posteriores reflejan un valor mas alto. Solo actualizara la entrada de la tabla di se ha determinado que la nueva ruta mas larga es estable.

Si un router falta o se corta una conexión de red, la red descubre esto por que el router deja de enviar o recibir actualizaciones, a lo largo de la conexión cortada. Si una ruta determina en la tabla de routing no se actualizara en seis ciclos de actualización sucesivos (180 segundos),un router *RIP* descartara esa ruta y permitiría que el resto de la red conozca el problema a través de sus propias actualizaciones periódicas.


## Versiones de RIP

Existen tres versiones de RIP:

- RIPv1
- RIPv2
- RIPng

*RIPv1*, es estandarizado en 1988, y *popularmente se le conoce como protocolo de enrutamiento con clase*, por que no envía información de mascara de subred en sus actualizaciones de routing.

*RIPv2*, estandarizado en 1988, se llama protocolo de enrutamiento sin clase, porque envía información de mascara de subred en sus actualizaciones de routing.

*RIPng*, esta es una extensión de *RIPv2* que se creo para admitir *IPv6*.


## Características 

Como se comento RIP utiliza una métrica por saltos, como forma para determinar la distancia de la red destino, por ejemplo:

Si el router vecino posee una red de desino y puede entregar paquetes directamente a la red de destino si utilizar ningún router, esa ruta solo tiene un salto. *En terminología esto se describe como un costo de uno*.

*RIP permite solo 15 saltos en una ruta*, si un paquete no puede llegar a un destino en 15 saltos, el destino se considera *inalcanzable*, pero a cada ruta podemos asignar un costo mas alto (como saltos adicionales). Por ejemplo:

Un enlace de respaldo satelital se le puede asignar un costo de 10 saltos para obligar al trafico a seguir otras rutas cuando la principal no se encuentre disponible. 

## Temporizadores RIP

![[Pasted image 20230105191614.png]]

Los temporizadores ayudan a regular el rendimiento, incluyen:

- *Temporizador de actualización (Update timer)*: Este controla la frecuencia con las actualizaciones de la tabla de routing, por defecto esta en *30 segundos*, *IP RIP* envía una copia completa de su tabla de routing, sujeta a un horizonte dividido (*por defecto hace esto cada 60 segundos*).

- *Temporizador no valido (Invalid timer)*: Ausencia de contenido actualizado en una actualización de routing, *RIP* espera *180 segundos* para marcar una ruta como no valida e inmediatamente la pone en espera.

- *Temporizadores de retención y actualizaciones activadas (hold-down timers & triggered updated)*: Estas ayudan con la estabilidad de rutas en el entorno de *Cisco*. Las suspensiones aseguran que los mensajes de actualización regulares no causen un bucle de routing de manera inapropiada. El router no actúa sobre información nueva no superior durante un cierto periodo de tiempo (*180 segundos como tiempo de retención*).

- *Temporizador de purga (Flush timer)*: *RIP* espera *240 segundos* adicionales después de la retención antes de que realmente se elimine la ruta en la tabla de routing.


![[Pasted image 20230105193253.png]]

Otra característica de estabilidad para ayudar con los bucles de routing incluyen el envenenamiento de ruta. Un *route poisoning* es una forma en que un nodo de puerta de enlace le dice a sus puertas de enlace vecinas que una de las puertas de enlace ya no esta conectada.

Para esto, la puerta de enlace de notificación establece el numero de saltos a la puerta de enlace no conectada y lo modifica a un numero que indica *infinito*, lo que en términos simples significa "No puedo llegar ahí". *Dado que RIP permite hasta 15 saltos a otra puerta, establecer el conteo de saltos a 16 es equivalente de "infinito"*.


## Ventajas y desventajas de RIP

Las ventajas de *RIP* incluyen:

- Configuración factible.
- Fácil de comprender.
- Predominantemente libre de bucles.
- Garantizado para admitir casi todos los routers.
- Promueve el equilibro de carga.

Mientras que las desventajas son: 

- No siempre es libre de bucles
- Solo admite el equilibrio de carga de igual costo
- Puede producirse congestión
- Ancho de banda intensivo e ineficiente
- Las grandes redes conducen a una lenta convergencia.

Además, se prefiere *RIP* que a las rutas estáticas debido a su configuración simple y al hecho de que no requiere una actualización cada vez que cambia la topología. La desventaja de *RIP* es su mayor sobrecarga de red y procesamiento en comparación con el routing estático.

Al utilizar *RIP*, los usuarios pueden encontrase con varias limitaciones. por ejemplo *RIP* aumenta el trafico de red debido a las comprobaciones y actualizaciones que realiza en los routers vecinos cada 30 segundos. Además, dado que *RIP* solo actualiza los routers vecinos, las actualizaciones para routers no vecinos pueden olvidarse ya que la información no es accesible de inmediato.

Otra limitación de *RIP* es la aplicación de un conteo *máximo de 15 saltos*, como resultado, es posible que no se pueda acceder o alcanzar a los routers remotos en redes grandes.


## Configuración 

Bien usaremos la siguiente topología para aplicar RIP:

![[Pasted image 20230106084458.png]]

Ahora si observamos la tabla de routing tenemos del *router 0*, tendremos solo 3 rutas que son las que están conectadas directamente el router.

![[Pasted image 20230106084656.png]]

Ahora ya entrando a la configuración de *RIP*, primero entramos al modo de configuración con *RIP*:

	Router(config)# router rip

Ahora para le tenemos que indicar a cada router que redes o que rutas quiere compartir con *RIP*, para este caso serian todas las redes a las que esta conectado el *router 0*.

	Router(config-router)# network 192.168.1.0
	Router(config-router)# network 192.168.2.0
	Router(config-router)# network 192.168.5.0

Ahora una vez configurado el *router 0* pasemos con el *router 1*, y así sucesivamente con los demás routers.

	Router(config)# router rip
	Router(config-router)# network 192.168.3.0
	Router(config-router)# network 192.168.2.0
	Router(config-router)# network 192.168.6.0

*router 4*

	Router(config)# router rip
	Router(config-router)# network 192.168.6.0
	Router(config-router)# network 192.168.5.0
	Router(config-router)# network 192.168.4.0

Con esto los routers aparte de tener información de las 3 redes a las que cada router esta conectado directamente, van a aparecer redes en sus tablas de enrutamiento de redes que esta recibiendo a través de *RIP*.

Y tal como se comento en el *router 4* tenemos nuevas rutas, indicando que fueron aprendidas mediante *RIP*.

![[Pasted image 20230106085658.png]]

Bien con esto toda nuestra topología estaría conectada, sin embargo que pasaría si uno de estos enlaces se cae, aquí es donde entra la convergencia, *RIP* buscara otra ruta que puede llegar al destino, aun que no sea la mas optima.

![[Pasted image 20230106090516.png]]

Ahora si hacemos un *tracert* desde la *PC4* a la *PC1* veremos que va a llegar al destino pero lo va hacer desde los enlaces activos:

![[Pasted image 20230106090731.png]]

Si el enlace del *router 1* y el *router 4* vuelve a funcionar y realizamos un *tracert* nuevamente, veremos que toma el camino mas corto, es decir que los router han informado del cambio que se realizo en dicha ruta para actualizar su tabla de routing.

![[Pasted image 20230106091104.png]]

Listo.