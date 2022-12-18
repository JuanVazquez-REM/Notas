Este modo nos permite interceptar/capturar todos lo paquetes que se encuentran en transito.

	airmon-ng start wlan0
Iniciamos la interfaz de red en modo monitor

Respecto a algunos procesos que pueden interrumpir ciertas tareas al realizar un ataque serian los siguientes:

-dhclient *Es un servicio DHCP que se encargar de asignar una ip al dispositivo(Dirección Mac)*
-wpa_supplincant *Este servicio se encargar de que continuamente estemos conectados a la red wifi*


	killall dhclient wpa_supplicant
	||
	pkill dhclient && pkill wpa_supplicant
De esta manera podemos matar los procesos


Ahora cuando desactivemos el modo monitor y queramos navegar por internet se puede surgir algunos problemas por el tema de los procesos que matamos.

	service networking restart
Con esto se reiniciara el networking y se reiniciaran los procesos


Ahora cuando iniciamos el modo monitor con arimon-ng, la propia herramienta detecta los procesos que resultan conflictivos, es por esto que la herramienta cuenta con su propio comando

	airmon-ng check kill
