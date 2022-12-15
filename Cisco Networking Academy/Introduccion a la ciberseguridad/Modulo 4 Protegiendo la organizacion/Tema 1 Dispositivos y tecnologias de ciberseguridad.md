Es este apartado se habla de como pueden proteger una organizacion con dispositivos de cisco y tecnologias.

## Dispositivos de seguridad
Estos pueden ser dispositivos fisicos o software que requiera estos, se pueden dividir es seis categorias.

- *Routers*
A pezar de que estos se utilizan para interconectar dispositivos, proporcionan un cifrado al trafico que generamos.
- *Firewall*
Este analiza el trafico y filtra dependiendo de sus reglas este puede prevenir comportamientos maliciosos.
- *Sistema de prevencion de intrusion (IPS)*
Este vigila la red de actividad maliciosa o cualquier actividad que intente explotar una vulneravilidad conocida.
- *Redes privadas virtuales (VPN)*
Estos crean un tunel cifrado haciendo segura la conexion remota a algun red o organizacion.
- *Antimalware o Antivirus*
Es un software que analiza el comportamiento de aplicacion en busca de actividad maliciosa y la deteccion de codigo malicioso.



## Cortafuegos (firewall)
Estos son diseñados para filtrar la comunicacion de un dispositivo a otro, este puede en una computadora para protegerse a si misma (*firewall basado en host*) o para proteger todo a una red.
Aun que con el tiempo se han creado firewalls con diferentes finalidades

- *Cortafuegos de la capa de red*
Este filtra la comunicacion dependiendo de la ip origen y destino.
- *Cortafuegos de la capa de transporte*
Filtra la comunicacion dependiendo de los puertos de datos de origen y destino.
- *Cortafuegos de la aplicacion*
Este filtra la comunicacion en funcion de un aplicacion o servicio.
- *Cortafuegos de capa sensible al contexto*
Este filtra comunicaciones segun el usuario, dispositivo, tipo de aplicacion y perfil de amenaza.
- *Servidor proxy*
Este filtra las solicitudes de un contenido web, como urls, nombre de dominios y tipos de medios.
- *Servidor proxy inverso*
Este se pone por delante de el servidor web para proteger, filtrar y distribuyen el acceso al servidor web
- *Cortafuegos de traduccion de direcciones de red (NAT)*
Estos enmascaran o ocultas las direcciones ip privadas de los hosts en la red.
- *Cortafuegos basado en host*
Estos filtran los puertos y llamadas a los servicios de un sistema operativo.

## Analisis de puertos
En redes, a cada aplicacion que se ejecuta en un dispositivo se le establece un identificador a este se el es llamado puerto, este puerto se establece en ambos extremos de la coneccion para establecer una conexion correctamente.

*El escaneo de puertos consiste en identificar que puertos estan abiertos en un dispositivo, puede utilizarse de forma malisiosa para identificar el SO y servicio que se ejecuta en un host o de forma ofensiva para verificar las politicas de seguridad en la red.*

Para esto existe *nmap* que es de las mas conocidas en internet para el escaneo de puertos, ya que tiene multiples opciones para adecuarse en cualquier entorno. 

## Sistemas de deteccion y prevencion de intrusion
Estos son sistemas de seguridad que se implentan para detedtar y prevenir actividades maliciosas, tales como los *sistemas de deteccion de intrusion* (IDS) y *los sistemas de prevencion de intrusiones* (IPS).

***IDS***
Este puede ser un dispositivo de red dedicado o varias herramientas en un servidor, firewall o incluso un *SO* de computadora como *windows* o *linux*, el objetivo de este es comparar el trafico contra una base de datos o firma de ataques para encontrar alguna similitud y con esto detectar algun comportamiento malicioso.

Si se detecta una coicidendia el *IDS* solo registara la deteccion y creara una alerta para un administrador de la red, *este no tomara medidas, por lo tanto esto no evitara que ocurran ataques, el trabajo del IDS es simplemente detectar, registrar y generar informes.* 

El analisis que realiza un *IDS* relentiza la red (esto de denomina como latencia). Para evitar estos retrasos en la red un *IDS* generalemente se coloca fuera de la linea de red normal. El trafico de duplica mediante un *switch* y luego se envian al *IDS*.

![[Pasted image 20221213160641.png]]

***IPS***
Este a comparacion del *IDS* puede bloquear o denergar el trafico segun la concidencia de una firma, uno de los *IPS/IDS* mas conocidos en el mercado en *Snort* es *Sourcefire de Cisco*. *Sourcefire* tiene la capacidad de realizar *analisis de trafico y de puertos en tiempo real*, registra, busca y compara el trafico, haciendo que puede *identificar sondas, ataques y escaneo de puertos.*

Tambien se integra con otras herramientas para informes y analisis de registro.
![[Pasted image 20221213181101.png]]

## Deteccion en tiempo real
Hoy en dia muchos de las organizacion so pueden detectar lo ataques que reciben hasta dias o incluso meses despues.

La deteccion de ataques a tiempo real requiere de mucho analisis activo, mediante el uso de firewall y dispositivos de red *IDS/IPS*. Tambien como herramientas de *deteccion de malware de servidores y cliente con conexiones a centros de amenazas globales en linea*.

*DDoS* es una de las mayores amanezas y ataques que requiere una deteccion y respuesta en tiempo real. Ya que la mayoria de estos niegan la disponibilidad a usuarios legitimos y es *dificil de defenderse contra estos ataques por que facilmente estos pueden ser una botnet de cientos o miles de host y los ataques aparecen como trafico legitimo*.


## Proteccion contra software malicioso
Una forma de protegerse con tra el software malicioso, los ataques de dia cero y las amenzas persistentes (APT) *se utiliza una solucion de deteccion de malware avanzado a nivel empresarial*, como la red de amenzas de proteccion contra malware *avanzada (AMP) de Cisco*.

Este software de cliente/servidor que se puede implementar en un servidor independiende o en otros dispositivos de la red, *este analiza millinoes de archivos y los correlaciona con cientos de millones de otros artefactos de malware analizado en busca de comportamientos que revelen una APT*.

Conoce mas sobre *Threat Grid de Cisco*.

**1. Equipo del centro de operaciones seguras**
Threat Grid permite al equipo de Cisco Secure Operations Center recopilar datos más precisos y procesables.

**2. Equipo de respuesta a incidencias**
Por lo tanto, el equipo de respuesta a incidentes tiene acceso a información forense sólida a partir de la cual puede analizar y comprender más rápidamente los comportamientos sospechosos.

**3. Equipo de inteligencia de amenazas**
Con este análisis, el equipo de inteligencia de amenazas puede mejorar de manera proactiva la infraestructura de seguridad de la organización.

**4. Equipo de ingenieria de infraestructura de seguridad**
En general, el equipo de ingeniería de infraestructura de seguridad puede consumir y actuar sobre la información de amenazas más rápido, a menudo de forma automatizada.


## Mejores practicas de seguridad

Muchas organizaciones nacionales y profecionales han publicado listas de buenas practicas de seguridad. Algunas de las pautas maS utiles se encuentran en repositorios origanizacionales como el centro de recursos de seguridad informatica del Instituto Nacional de Estadares y Tecnologia (NIST)

- **Realizar una evaluacion de riegos**
Conocer y omprender el valor de lo que esta protegiendo ayudara a justificar los gastos de seguridad.

- **Crea una politica de seguridad**
Crea una politica que describa claramente las reglas, los roles laborales y las responsabilidades y expectativas de los empleados de la organizacion.

- **Medidas de seguridad fisicas**
Restrinja el acceso a los armarios de redes y la ubicaciones del servidor, asi como la extincion de incendios.

- **Medidas de seguridad de recursos humanos**
Las verificaciones de antecedentes deben completarse para todos los empleados.

- **Realice y pruebe copias de seguridad**
Realice copias de seguridad de la informacion con regularidad y pruebe la recuperacion de datos a partir de copias de seguridad.

- **Mantega actulizaciones y parches de seguridad**
Actulice periodicamente los programas y sistemas operativos de los servidores, cientes y  dispositivos de red.

- **Emplee controles de acceso**
Configure los roles de usuario y los niveles de privilegio, asi como autenticacion de usuario solida.

- **Pruebe regularmente la respuesta a incidentes**
Utilice un equipo de respuestas ante incidentes y pruebe los escenarios de respuesta ante emergencias.

- **Implementa una herramienta de administracion, analisis y monitoreo de redes**
Elija una solucion de monitoreo de seguridad que se integre en otras tenologias.

- **Implemente dispositivos de seguridad de red**
Utilice enrutadores, firewalls y otros dispositivos de seguridad de proxima generacion.

- **Implemente una solucion interal de seguridad para enpoints**
Utilice software antivirus y antimalware en el nivel de la empresa.

- **Eduque a los usuarios**
Proporcione capacitacion a los empleados en procedimientos de seguridad.

Una de las organizaciones mas conocidas y respetadas para la capacitacio en ciberseguridad es el *SANS Institute*. Si desea saber mas informacion sobre esto visite [SANS y los tipos de capacitacion y certificaciones que ofrecen](https://www.sans.org/about/). 

- **Cifrar datos**
Cifre todos los datos organizativos confidenciales, incluido el correo electronico.
