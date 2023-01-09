Como bien sabemos existen múltiples protocolos de enrutamiento tanto a *nivel interno (IGP)* con un *nivel externo (EGP)*, en este apartado hablaremos de BGP como protocolo de enrutamiento a nivel externo.

Te recomiendo que leas las [[10. Diferencias entre IGP y EGP|Diferencias entre IGP y EGP]], para comprender mejor lo anterior y por ahí se da una breve introducción a *EGP*.

Bien dicho esto ¿Qué es *BGP*?
*Border Gateway Protocol* es un protocolo dinámico escalable, el cual es usado en internet por grupos de enrutadores para compartir información de enrutamiento.

*BGP* dirige los paquetes entre [[Sistemas atonomos (AS)]], que son redes destinadas por una única empresa o proveedores de servicios de internet (ISP).

Los proveedores de servicios de internet (*ISP*) que trabajan con redes IP tienen en claro que *BGP es el protocolo de internet mas complejo y difícil de configurar*. Sin embargo, su *énfasis es la seguridad y la escalabilidad lo hace esencial*.

## Como funciona BGP
Un dominio de routing independiente, que casi siempre significa una red *ISP*, se denomina sistema autónomo. *BGP* siempre se usa como el protocolo de routing de elección entre diferentes *ISP*, lo que se conoce como *BGP* externo.

Para permitir la transferencia de información de routing entre *ISP* vecinos, *BGP* requiere acuerdos de pares, que comprende los términos y condiciones necesarios para el intercambio de trafico. El protocolo se adhiere a estos acuerdos mientras que evalúa las tablas de routing.

Lo hace utilizando un algoritmo de selección que determina la mejor ruta para dirigir el trafico, sin embargo, el mejor camino no suele ser la ruta mas corta.

Todos los demás protocolos de routing se ocupan únicamente de encontrar la ruta mas optima hacia todos los destinos conocidos. *BGP no puede adoptar este enfoque simplista por que los acuerdos de pares entre ISP casi siempre resultan en políticas de routing complejas.* Para ayudar a los operadores de red a implementar estas políticas, BGP lleva una gran cantidad de atributos con cada prefijo, incluidos los siguientes:

- *La ruta del sistema autónomo (AS)* es la ruta completa que documenta los sistemas autónomos por los que un paquete tendría que viajar para llegar al destino.
- *La preferencia local* es el costo interno de un destino, que se utiliza para garantizar la coherencia en todos el AS.
- *El discriminador de múltiples salidas (MED)* les da a los *ISP* adyacentes la posibilidad de preferir un punto de interconexión sobre otro.
- *Comunidades* es un conjunto de etiquetas genéricas que pueden indicar varias políticas administrativas entre routers *BGP*.

*Debido a la complejidad inherente de BGP, los clientes y los ISP pequeños a menudo implementan BGP solo donde es necesario*, por ejemplo en punto de interconexión y en un subconjunto minino de routers centrales, a los que se encuentran entre los puntos de interconexión.

## Problemas con el protocolo BGP
*BGP se origino en 1989 como una solución rápida para internet*, pero se a mantenido como el protocolo principal para el trafico de larga distancia, *y como todo, las amenazas informáticas en evolucionado y BGP no a seguido el ritmo*.

El abuso de *BGP* se llama *BGP hijacking*, que es posible por que el protocolo se basa en confiar en las rutas anunciadas. *Ha habido múltiples intentos de crear una versión mas segura de BGP, pero la implantación es extremadamente problemática*, ya que la mayoría de las nuevas versiones no pueden comunicarse con BGP estándar,
*lo que significa que todos los AS del mundo tendrían que adoptar el nuevo protocolo simultáneamente*.

Estos son algunos de los incidentes de BGP:

- *2004 TTNet*, un ISP turco, *anuncio malas rutas BGP que afirmaban que eran el mejor destino para todo el trafico en internet*. El problema solo duro un día, pero muchas personas en todo el mundo no pudieron acceder a internet.

- 2008, un ISP Paquistán *intento bloquear el acceso de los usuarios paquistaníes a YouTube enrutando el trafico a un agujero negro*. La ruta se anuncio accidentalmente a los routers vecinos que propagaron la ruta en todo el mundo. *En este caso YouTube estuvo inaccesible durante varias horas*.

- 2018, *los atacantes crearon deliberadamente malas rutas BGP* para redirigir el trafico destinado al servicio DNS de Amazon, para redirigir el trafico a ellos mismos, *así pudieron robar $1,939,360.10 de criptomonedas.*


## Configuración
Al configurar *BGP* se sigue prácticamente el mismo procedimiento que las demás protocolos de enrutamiento dinámicos solo con la diferencia que *BGP* no suele encontrar vecinos por si solo, si no que hay que registrar los vecinos que tiene.

Teniendo como ejemplo la siguiente topología, realizaremos los siguientes pasos:

1. Asignar *ID-AS*.
2. Añadir redes.
3. Agregar vecinos.


![[Pasted image 20230106162217.png]]

Por el ejemplo, en cada router tendrá un *ID-AS*.

- *router 0 ID-AS 200*
- *router 1 el ID-AS 300*
- *router 2 el ID-AS 100*

Para configurar esto se utiliza el siguiente comando y posteriormente entramos en un modo de configuración BGP en el router, donde aquí, se agregaran las redes:

*Router 0*

	Router(config-if)# router bgp 200
	//agregamos las redes
	Router(config-router)# network 192.168.56.0 mask 255.255.255.0
	Router(config-router)# network 10.0.0.0 mask 255.255.255.252

*Router 2* agregaremos igualmente la redes

	Router(config-if)# router bgp 100
	//agregamos las redes
	Router(config-router)# network 10.0.0.0 mask 255.255.255.252
	Router(config-router)# network 10.0.0.4 mask 255.255.255.252 

*Router 1* agregaremos igualmente la redes

	Router(config-if)# router bgp 300
	//agregamos las redes
	Router(config-router)# network 192.168.0.0 mask 255.255.255.0
	Router(config-router)# network 10.0.0.4 mask 255.255.255.252
	Router(config-router)# network 10.0.0.8 mask 255.255.255.252

Una vez hecho esto, si realizamos un ping desde *PC1* a cualquier otro dispositivo de la topología este será inaccesible, a menos de ser el router por el cual esta conectado directamente.

Es por esto que nos faltaría que cada uno de los routers conozca sus vecinos. Para agregar los vecinos seria el siguiente comando:

	neighbor <ip-address> remote-as <#>

*Router 0*

![[Pasted image 20230106172309.png]]

	Router(config-router)# neighbor 10.0.0.2 remote-as 100
	Router(config-router)# neighbor 10.0.0.10 remote-as 300

*Router 2* agregaremos sus vecinos.

![[Pasted image 20230106172436.png]]

	Router(config-router)# neighbor 10.0.0.1 remote-as 200
	Router(config-router)# neighbor 10.0.0.6 remote-as 300

*Router 1* de igual forma agregamos sus vecinos.

![[Pasted image 20230106172551.png]]

	Router(config-router)# neighbor 10.0.0.5 remote-as 100
	Router(config-router)# neighbor 10.0.0.9 remote-as 200

Con el siguiente comando podremos ver toda la información del enrutamiento *BGP*.

	Router# show bgp neighbors

Ah este punto toda nuestra topología esta comunicada con *BGP*.


