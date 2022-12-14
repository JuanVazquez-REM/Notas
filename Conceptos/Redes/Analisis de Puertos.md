[[Nmap]] es una de las muchas herramientas para el escaneo de puerto, pero es de las mas eficientes, la orden mas sencilla es ` nmap <objetivo> ` analiza mas de 1660 puertos [[Protocolos de Internet # TCP IP]], y aquí esta lo interesante muchos analizadores clasificaron que un puerto solo puede tener dos estados **abierto o cerrado**.

Pero nmap es mucho mas descriptivo, los puertos se dividen en seis estados:
- Abierto
- Cerrado
- Filtrado
- No filtrado
- Abierto | filtrado 
- cerrado | filtrado

Por ejemplo un análisis con nmap en la misma red donde se encuentra el objetivo puede mostrarse el puerto 135/tcp abierto, mientras que si se realiza el mismo escaneo pero desde internet este se puede representar como filtrado.

**Abierto**
Puerto abierto es decir que una aplicación acepta conexiones TCP o UDP por el puerto,*las personas orientadas a la ciberseguridad saben que cada puerto abierto puede ser un vector de ataque*, los administradores intentan cerrar o aplicar un firewall a estos para protegerlos, pero sin dejar a los usuarios con acceso a estos, y por otro lado de la seguridad un puerto abierto puede indicar el servicio que se provee.

**Cerrado**
Un puerto cerrado es accesible, *es decir que recibe y responde a nmap, pero no existe ninguna aplicación escuchando el puerto*, estos pueden ser útiles para determinar si una maquina esta activa o no, los puertos cerrados son alcanzables o sea que no están filtrados, puede ser de utilidad estar escuchando un puerto si el administrador lo abre en determinados lapsos, *los administradores pueden considerar bloquear estos puertos con un firewall, a estos se les llama filtrados*.

**Filtrado**
Nmap menciona que no puede determinar si un puerto esta abierto si *se aplica algún filtrado de paquetes que previene que las sondas de nmap lleguen al puerto*, el filtrado puede provenir de dispositivos de firewall dedicados, de las reglas del enrutador, o por una aplicación de firewall instalada en el equipo.

Estos puertos suelen proporcionar muy poca informacion. A veces responden con un mensaje de error [[ICMP]] del tipo 3, código 13 (*Destino inalcanzable: comunicación prohibida por administradores*). Esto fuerza a nmap a reintentar varias veces, considerando que la sonda pudo haberse descartado por la congestión de la red, en vez de haberse filtrado. *Esto ralentiza considerablemente el escaneo*.

**No Filtrado**
Esto indica que el puerto es accesible, pero nmap no puede determinar si esta abierto o cerrado.
*Solamente el sondeo ACK, utilizado para determinar las reglas de un firewall, clasifica a los puertos según este estado*. El analizar puertos no filtrados con otro tipos de análisis, como el sondeo Windows, SYN o FIN, pueden ayudar a determinar si el puerto se encuentra abierto.

**Abierto | Filtrado**
Nmap marca los puertos en este estado, cuando no puede determinar si un puerto esta abierto o cerrado, *es decir que los puertos abiertos no responden.*

La ausencia de una respuesta puede determinar que un filtro de paquetes ha descartado la sonda, o que se elimina cualquier tipo de respuesta asociada, es por eso que nmap no puede determinar si esta abierto o filtrado. *Los sondeos UDP, protocolo IP, FIN, Null, y Xmas clasifican a los puertos de esta manera.*

**Cerrado | Filtrado**
Este estado se utiliza cuando Nmap no puede determinar si un puerto se encuentra cerrado o filtrado, y puede aparecer aparecer sólo durante un *sondeo IPID pasivo*.