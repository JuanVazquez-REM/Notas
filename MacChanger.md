# Macchanger
Machanger lo que nos permite es alterar nuestra direccion mac, generando una aleatoriamente,con la opcion de volver a tu mac original.


	sudo ifconfig eth0 down
Primero debemos de desactivar la interfaz de red a la que vamos c cambiar la mac, finalizando el cambio de mac debe de activar la interfaz. 

	macchanger -r eth0
Genera una mac totalmente aleatoria.

	macchanger --mac xx:xx:xx:xx: eth0
Si deseamos cambiar la mac manualmente.

	macchanger -p eth0 
Para volver a la su valor de hardware original y permanente la mac.

	sudo ifconfig eth0 up
Habilitamos la interfaz de red despues de los cambios.

### Opciones 

	macchanger -e eth0
Para **aleatorizar solo los bytes específicos del dispositivo de la dirección MAC actua**l (es decir, si la dirección MAC estuviera marcada, aún se registraría como del mismo proveedor)