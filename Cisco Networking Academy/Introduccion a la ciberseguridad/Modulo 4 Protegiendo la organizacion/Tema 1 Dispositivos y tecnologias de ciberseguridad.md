Es este apartado se habla de como pueden proteger una organización con dispositivos de cisco y tecnologías.

## Dispositivos de seguridad
Estos pueden ser dispositivos físicos o software que requiera estos, se pueden dividir es seis categorías.

- *Routers*
A pesar de que estos se utilizan para interconectar dispositivos, proporcionan un cifrado al trafico que generamos.
- *Firewall*
Este analiza el trafico y filtra dependiendo de sus reglas este puede prevenir comportamientos maliciosos.
- *Sistema de prevención de intrusión (IPS)*
Este vigila la red de actividad maliciosa o cualquier actividad que intente explotar una vulnerabilidad conocida.
- *Redes privadas virtuales (VPN)*
Estos crean un túnel cifrado haciendo segura la conexión remota a algún red o organización.
- *Antimalware o Antivirus*
Es un software que analiza el comportamiento de aplicación en busca de actividad maliciosa y la detección de código malicioso.



## Cortafuegos (firewall)
Estos son diseñados para filtrar la comunicación de un dispositivo a otro, este puede en una computadora para protegerse a si misma (*firewall basado en host*) o para proteger todo a una red.
Aun que con el tiempo se han creado firewalls con diferentes finalidades

- *Cortafuegos de la capa de red*
Este filtra la comunicación dependiendo de la ip origen y destino.
- *Cortafuegos de la capa de transporte*
Filtra la comunicación dependiendo de los puertos de datos de origen y destino.
- *Cortafuegos de la aplicación*
Este filtra la comunicación en función de un aplicación o servicio.
- *Cortafuegos de capa sensible al contexto*
Este filtra comunicaciones según el usuario, dispositivo, tipo de aplicación y perfil de amenaza.
- *Servidor proxy*
Este filtra las solicitudes de un contenido web, como urls, nombre de dominios y tipos de medios.
- *Servidor proxy inverso*
Este se pone por delante de el servidor web para proteger, filtrar y distribuyen el acceso al servidor web
- *Cortafuegos de traducción de direcciones de red (NAT)*
Estos enmascaran o ocultas las direcciones ip privadas de los hosts en la red.
- *Cortafuegos basado en host*
Estos filtran los puertos y llamadas a los servicios de un sistema operativo.

## Análisis de puertos
En redes, a cada aplicación que se ejecuta en un dispositivo se le establece un identificador a este se el es llamado puerto, este puerto se establece en ambos extremos de la conexión para establecer una conexión correctamente.

*El escaneo de puertos consiste en identificar que puertos están abiertos en un dispositivo, puede utilizarse de forma maliciosa para identificar el SO y servicio que se ejecuta en un host o de forma ofensiva para verificar las políticas de seguridad en la red.*

Para esto existe *nmap* que es de las mas conocidas en internet para el escaneo de puertos, ya que tiene múltiples opciones para adecuarse en cualquier entorno. 

## Sistemas de detección y prevención de intrusión
Estos son sistemas de seguridad que se implementan para detectar y prevenir actividades maliciosas, tales como los *sistemas de detección de intrusión* (IDS) y *los sistemas de prevención de intrusiones* (IPS).

***IDS***
Este puede ser un dispositivo de red dedicado o varias herramientas en un servidor, firewall o incluso un *SO* de computadora como *windows* o *Linux*, el objetivo de este es comparar el trafico contra una base de datos o firma de ataques para encontrar alguna similitud y con esto detectar algún comportamiento malicioso.

Si se detecta una coincidencia el *IDS* solo registrara la detección y creara una alerta para un administrador de la red, *este no tomara medidas, por lo tanto esto no evitara que ocurran ataques, el trabajo del IDS es simplemente detectar, registrar y generar informes.* 

El análisis que realiza un *IDS* ralentiza la red (esto de denomina como latencia). Para evitar estos retrasos en la red un *IDS* generalmente se coloca fuera de la linea de red normal. El trafico de duplica mediante un *switch* y luego se envían al *IDS*.

![[Pasted image 20221213160641.png]]

***IPS***
Este a comparación del *IDS* puede bloquear o denegar el trafico según la coincidencia de una firma, uno de los *IPS/IDS* mas conocidos en el mercado en *Snort* es *Sourcefire de Cisco*. *Sourcefire* tiene la capacidad de realizar *análisis de trafico y de puertos en tiempo real*, registra, busca y compara el trafico, haciendo que puede *identificar sondas, ataques y escaneo de puertos.*

También se integra con otras herramientas para informes y análisis de registro.
![[Pasted image 20221213181101.png]]

## Detección en tiempo real
Hoy en día muchos de las organización so pueden detectar lo ataques que reciben hasta días o incluso meses después.

La detección de ataques a tiempo real requiere de mucho análisis activo, mediante el uso de firewall y dispositivos de red *IDS/IPS*. También como herramientas de *detección de malware de servidores y cliente con conexiones a centros de amenazas globales en linea*.

*DDoS* es una de las mayores amenazas y ataques que requiere una detección y respuesta en tiempo real. Ya que la mayoría de estos niegan la disponibilidad a usuarios legítimos y es *difícil de defenderse contra estos ataques por que fácilmente estos pueden ser una botnet de cientos o miles de host y los ataques aparecen como trafico legitimo*.


## Protección contra software malicioso
Una forma de protegerse contra el software malicioso, los ataques de día cero y las amenazas persistentes (APT) *se utiliza una solución de detección de malware avanzado a nivel empresarial*, como la red de amenazas de protección contra malware *avanzada (AMP) de Cisco*.

Este software de cliente/servidor que se puede implementar en un servidor independiendo o en otros dispositivos de la red, *este analiza millones de archivos y los correlaciona con cientos de millones de otros artefactos de malware analizado en busca de comportamientos que revelen una APT*.

Conoce mas sobre *Threat Grid de Cisco*.

**1. Equipo del centro de operaciones seguras**
Threat Grid permite al equipo de Cisco Secure Operations Center recopilar datos más precisos y procesables.

**2. Equipo de respuesta a incidencias**
Por lo tanto, el equipo de respuesta a incidentes tiene acceso a información forense sólida a partir de la cual puede analizar y comprender más rápidamente los comportamientos sospechosos.

**3. Equipo de inteligencia de amenazas**
Con este análisis, el equipo de inteligencia de amenazas puede mejorar de manera proactiva la infraestructura de seguridad de la organización.

**4. Equipo de ingeniería de infraestructura de seguridad**
En general, el equipo de ingeniería de infraestructura de seguridad puede consumir y actuar sobre la información de amenazas más rápido, a menudo de forma automatizada.


## Mejores practicas de seguridad

Muchas organizaciones nacionales y profesionales han publicado listas de buenas practicas de seguridad. Algunas de las pautas mas útiles se encuentran en repositorios organizacionales como el centro de recursos de seguridad informática del Instituto Nacional de Estándares y Tecnología (NIST)

- **Realizar una evaluación de riegos**
Conocer y comprender el valor de lo que esta protegiendo ayudara a justificar los gastos de seguridad.

- **Crea una política de seguridad**
Crea una política que describa claramente las reglas, los roles laborales y las responsabilidades y expectativas de los empleados de la organización.

- **Medidas de seguridad físicas**
Restrinja el acceso a los armarios de redes y la ubicaciones del servidor, así como la extinción de incendios.

- **Medidas de seguridad de recursos humanos**
Las verificaciones de antecedentes deben completarse para todos los empleados.

- **Realice y pruebe copias de seguridad**
Realice copias de seguridad de la informacion con regularidad y pruebe la recuperación de datos a partir de copias de seguridad.

- **Mantenga actualizaciones y parches de seguridad**
Actualice periódicamente los programas y sistemas operativos de los servidores, clientes y  dispositivos de red.

- **Emplee controles de acceso**
Configure los roles de usuario y los niveles de privilegio, así como autenticación de usuario solida.

- **Pruebe regularmente la respuesta a incidentes**
Utilice un equipo de respuestas ante incidentes y pruebe los escenarios de respuesta ante emergencias.

- **Implementa una herramienta de administración, análisis y monitoreo de redes**
Elija una solución de monitoreo de seguridad que se integre en otras tecnologías.

- **Implemente dispositivos de seguridad de red**
Utilice enrutadores, firewalls y otros dispositivos de seguridad de próxima generación.

- **Implemente una solución integral de seguridad para enpoints**
Utilice software antivirus y antimalware en el nivel de la empresa.

- **Eduque a los usuarios**
Proporcione capacitación a los empleados en procedimientos de seguridad.

Una de las organizaciones mas conocidas y respetadas para la capacitación en ciberseguridad es el *SANS Institute*. Si desea saber mas informacion sobre esto visite [SANS y los tipos de capacitación y certificaciones que ofrecen](https://www.sans.org/about/). 
 
- **Cifrar datos**
Cifre todos los datos organizativos confidenciales, incluido el correo electrónico.
