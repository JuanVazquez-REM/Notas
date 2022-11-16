Podemos capturar el trafico que ocurre en nuestro entorno con *tcpdump* y analizarla con [[Tshark]].

	tcpdump -i eth0 -w Captura.cap -v

Una vez capturado podemo realizar una traza ICMP desde mi maquina local a la maquina virtual, *en este caso mi maquina virtual esta utlizando la interfaz de red en modo puente, si lo hace desde NAT la ip host sera el host(router)*.

Analizamos el los paquetes con tshark, filtramos por json y por ultimo los campos que nos interezan.

	tshark -r CapturaICMP.cap -Y "icmp" -Tfields -e ip.host 2>/dev/null | head -n 1

La primer IP es el host, la segunda el destino.

Al igual que podemos interceptar peticiones POST y poder vizualizar los datos enviados en texto plano *solamente en http*.
