Podemos capturar el trafico que ocurre en nuestro entorno con *tcpdump* y analizarla con [[Tshark]].

	tcpdump -i eth0 -w Captura.cap -v

Una vez capturado podemos realizar una traza ICMP desde mi maquina local a la maquina virtual, *en este caso mi maquina virtual esta utilizando la interfaz de red en modo puente, si lo hace desde NAT la ip host será el host(router)*.

Analizamos el los paquetes con Tshark, filtramos por json y por ultimo los campos que nos interesan.

	tshark -r CapturaICMP.cap -Y "icmp" -Tfields -e ip.host 2>/dev/null | head -n 1

La primer IP es el host, la segunda el destino.

Al igual que podemos interceptar peticiones POST y poder visualizar los datos enviados en texto plano *solamente en http*.
