Machanger lo que nos permite es alterar nuestra dirección [[Direccion MAC | MAC]], generando una aleatoriamente, con la opción de volver a tu mac original.

Ahora podemos saber cual es la dirección mac de nuestra tarjeta de red, ya sea la permanente(De fabrica) o la actual que puede ser una falsificada.

	macchanger -s wlan0

Ahora podemos cambiar la dirección mac, con una mac aleatoria(Desconocida).
	macchanger -r wlan0
*Para cambiar la mac, siempre tenemos que tener nuestra tarjeta de red deshabilitada.*
	sudo ifconfig wlan0 down
*Una vez cambiada levantaremos nuevamente la tarjeta de red.*
	sudo ifconfig wlan0 up

Ahora si bien sabemos podemos generar una dirección MAC suplantando el OUI, para creer ser otro proveedor, como la NSA.

Con macchanger podemos ver un listado de todos lo proveedores que tiene registrados y ver su OUI e utilizarlos, por ejemplo la NSA.

	macchanger -l | grep "NATIONAL SECURITY AGENCY"

Después suplantamos el OUI, y el UAA lo creamos aleatoriamente.

	macchanger --mac xx:xx:xx:xx:xx eth0
Si deseamos cambiar la mac manualmente.

	macchanger -p eth0 
Para volver a la su valor de hardware original y permanente la mac.


### Opciones 

	macchanger -e eth0
Para **aleatorizar solo los bytes específicos del dispositivo de la dirección MAC actúa**l (es decir, si la dirección MAC estuviera marcada, aún se registraría como del mismo proveedor), es decir que solo cambia el **Identificador del producto (UAA)**.