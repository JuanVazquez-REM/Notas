# NMAP 
Se utiliza para escanear una red y sus puertos con el objetivo de obtener información importante sobre la misma para controlar y gestionar su seguridad. 

	nmap -sP -n 192.168.1.0/24
Realiza un escaneo por toda la red local proporcionandonos todas las maquinas activas en nuestra red local.

-sP *realiza un escaneo por icmp, que se realiza un ping por toda la red*
-n *evita la resolucion de nombre por lo tanto en mas rapida la ejecucion*	
 192.168.1.0/24 *es el rango de ip donde iniciara el escaneo* 

	nmap -p- -sV 192.168.1.68
Realiza un escaneo de todos los puertos habiertos en una maquina victima especifica donde proporciona puertos, tipo de servicio y la version del servicio que se utiliza en dicho puerto.

-p- *realiza un escaneo de todos los 65535 puertos que existen para saber cual se puede vulnerar *
-sV *es para que muestre la verision del servicio que se utiliza en dicho puerto*
192.168.1.69 *ip de la maquina donde se realizara el escaneo*

###### Parametros
--open *lista los parametros abiertos*
-T5 *[Timing Template](https://nmap.org/book/performance-timing-templates.html) modo insane*
-v *para que reporte los puertos abiertos por consola*
-n *quita la resolucion dns*
-p31000-32000 *rango de puertos a escanear*


Notas 
	Cuando se realiza una auditoria para una empresa o profecional lo
	recomendable es que no se realice un escaneo de todos los puertos 
	existentes ya que la red lo puede detectar como una amenaza, asi 
	que se recomienta escanear los puertos mas utlizados.
