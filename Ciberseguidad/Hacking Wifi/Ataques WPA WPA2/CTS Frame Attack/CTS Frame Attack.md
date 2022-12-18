Lo que se efectuara será la captura de la trama CTS para manipular la trama con una duración alta y enviarlos al AP masivamente para consumir los recursos del AP y mantener los canales demasiamos ocupados como para responder a los clientes legítimos.

![[Pasted image 20221021143641.png]]

Esto llevara a un secuestro de ancho de banda y posiblemente el usuario pase a des autenticarse de la red y volverse a autenticar y con esto tendremos un handshake.

![[Pasted image 20221021130823.png]]


## Attack
Para este primero necesitamos capturar un trazas CTS que halla sido enviado al AP victima.
Capturaremos el trafico con airodump-ng y lo guardaremos en un archivo.

	airodump-ng -w CapturasCTSFrame -c 6 --essid White wlan0mon

Dejado pasar un par de segundo paramos la captura y la abrimos con [[Tshark]], filtraremos por los paquetes CTS, que corresponde al siguiente filtro *wlan.fc.type_subtype\==28*.

	tshark -r CapturaCTSFrame -Y "wlan.fc.type_subtype==28" -Tfields wlan.duration 2>/dev/null | short -u
-r *Leer un archivo*
-Y *Aplicar un filtro*
-Tjson *Filtra toda la informacion en json*
-Tfields  -e wlan.duration *Filtra por un campo*
-short -u *Ordena y solo deja campos únicos*

Para mayor comodidad lo abrimos con [[WireShark]] en segundo plano(proceso hijo).

	wireshark CapturaCTSFrame > /dev/null 2>&1 &

Aplicamos un ```disown``` para que este proceso se convierta en un proceso padre y no dependa de nadie.
Después aplicamos el filtro para lo trama CTS *wlan.fc.tyoe_subtype\==28* y exportamos dicho trama seleccionado.
Posteriormente vamos a editar la duración de este trama, estas tramas se encuentra en hexadecimal por lo tanto tenemos que abrirlo en ese formato.

	apt install ghex -y
ghex no permite interpretar el hexadecimal

	ghex ctsframe > /dev/null 2>&1 &
	disown

![[Pasted image 20221024074604.png]]
Ahora si modificaremos el campo de duración recordando la estructura del trama CTS.

![[Pasted image 20221021130823.png]]
Los últimos 6 pares seria la dirección MAC del AP y después los 2 pares de la duración, pero estos 2 pares están 00 00, esto es por que la trama de capturo con *airodump-ng* y aquí pueden salir falso-positivos como sucedió aquí.

Es por eso que se debe de capturar la trama por WireShark, para esto abrimos WireShark y analizamos la red hasta encontrar un CTS para después exportarlo como *.pcap*.

Como se puede observar en WireShark tiene un preview del paquete en hex, y aquí podemos ver mas claro donde se encuentra la duración.
![[Pasted image 20221024080653.png]]
84 00 estos pares serian la duración, pero esto se lee a la inversa 00 84, verifiquemos lo en python3

	python3
	0x0084

Ahora la intención es modificar esta duración para que la trama dure 30,000 microsegundos como valor tope, para esto debemos de convertir este valor a hexadecimal e insertarlo en la trama capturada.

	python3
	hex(30000)
	output: 0x7530

![[Pasted image 20221024081707.png]]

Ahora recordando de los 6 últimos pares son la dirección MAC del destino, vamos a reemplazarla por la MAC de quien queremos atacar.

Después abrimos el frame con WireShark para ver posibles advertencias, eso dejaría en claro si lo modificamos correctamente.
![[Pasted image 20221024082617.png]]
Y bien una vez hecho esto nuestra trama esta lista para ser enviada.

Para esto utilizaremos la herramienta *tcpreplay* que nos permite replicar trazas TCP.

	tcpreplay --intf1=wlan0mon --topspeed --loop=2000 ctsframe.pcap 2>/dev/null

--intf1= *Asignamos la tarjeta de red*
-\-topspeed *Para enviar los paquetes a la máxima velocidad y no esperar a que se envié un paquete y después otro sucesivamente*
-\-loop=2000 *Bucle de 2000 es decir 2000 trazas enviadas*
ctsframe.pcap *La trama enviada*

Con esto se congestionara la red y provocar un expulsión de usuarios legítimos.
