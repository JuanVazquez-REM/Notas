## Seguridad basada en el comportamiento
Es una forma de deteccion de amenazas que implica capturar y analizar el flujo de comunicacion entre un usuario en la red local y un destino local o remoto. Cualquier cambio en los patrones normales de comportamiento se considera anomalia y puede indicar un ataque.

Herramientas de deteccion basadas en el comportmiento.

- **Honeypot**
Esta herramienta atrae al atacante apelando a su patro predicho de comportamiento malicioso. Una vez que el atacante este dentro del honeypot, el administrador de la red puede capturar, registrar y analizar su comportamiento para poder construir una mejor defensa.

- **Arquitectura de la solucion Cisco Cyber Threat Defense**
Esta arquitectura es utilizada para la deteccion e indicadores basados en el comportamiento para proporcionar mayor visibilidad, contexto y control. El objetivo es saber quien esta llevando a cabo el ataque, que tipo de ataque estan realizando y donde, cuando y como se esta produciendo el ataque. 

Esta arquitectura de seguridad utiliza muchas tecnologias de seguridad para lograr este objetivo.

### NetFlow
Esta tecnologia se utiliza para recopilar informacion sobre los datos que fluyen a traves de una red, *incluidos quienes y que dispositivos estan en la red, cuando y como los usuarios y los dispositivos acceden a la red.*

NetFlow es un componente importante en el analisis de la deteccion basados en el comportamiento. *Los conmutadores, enrutadores y firewalls equipados con NetFlow pueden reportar informacion sobre la entrada , salida y viaje de datos a traves de la red.*

Esta informacion se envia a los recopiladores de NetFlow que recopilan, *almacenan y analizan datos de NetFlow*, que se pueden utilizar para establecer comportamientos de referencia en mas de 90 atributos, como la direccion IP de origen y destino.

![[Pasted image 20221213203750.png]]


## Pruebas de penetracion 
Estas pruebas son el acto de evaluar un sistema informatico, una red o una organizacion en busca de vulnerabilidades de seguridad. Una prueba de penetracion busca violar los sistemas, las personas, los procesos y el codigo para descubrir vulnerabilidades que podrian explotarse. Esta informacion se utiliza para mejorar las defensas del sistema y garantiar que puedan resistir mejor los ciberataques en el futuro.

***Procesos***

**1. Planificacion**
En en esta etapa se recopila la mayor informacion posible sobre un sistema o red de destino, sus posibles vulnerabilidades y exploits para usarlo en su contra. Esto implica llevar a cabo un *reconocimiento pasivo o activo (hueva)* e investigacion de vulnerabilidad. 

**2. Escaneo**
En esta etapa se lleva a cabo un reconocimiento activo para sondear un sistema o red objetivo e identificar posibles debilidades que, si se explotan, podrian dar acceso a un atacante. El reconocimiento activo puede incluir:

- Escaneo de puertos para identificar puntos de acceso potenciales en un sistema de destino.
- Analisis de vulnerabilidades para identificar posibles vulnerabilidades explotables de un objetivo en particular.
- Establecer una conexion activa con un destino (enumeracion) para identificar la cuenta de usuario, la cuenta del sistema y cuenta del administrador.

**3. Obtener acceso**
Uno de los objetivos de las pruebas de penetracion es obtener acceso al sistema destino y rastrear el trafico de la red, utilizando varios metodos para explotar el sistema, que incluyen:

- Lanzar exploits con carga util en sistema (payload).
- Transpasar las barreras fisicas a los activos.
- Ingenieria social.
- Explotar las vulnerabilidades del sitio web.
- Explotar vulnerabilidades o configuraciones incorrectas en el software y hardware.
- Violacion de los controles de acceso.
- Descifrar Wi-Fi encriptado debil.

**4. Mantener el acceso**
La puebra mantendra el acceso al objetivo para averiguar que datos del sistema son vulnerables a la explotacion. *Es importante que permanezca sin ser detectados*, por lo general, utilizando puertas traceras, cabellos de troya, rootkits y otros canales encubiertos para ocultar su presencia.

Cuando esta infraestructura este en su lugar, la prueba procedera a recopilar los datos que se concideren valiosos.

**5. Analisis y reportes**
Proporcionar comentarios a travez de un informe que recomienda actualizaciones de los productos, las politicas y la capacitacion para mejorar la seguridad de la organizacion.


## Reduccion del impacto
Si bien entedemos que las organizaciones son el mayor foco de ataques y estas hacen el mayor esfuerzo para prevenir estos ataques es inebitable ser atacados ya que ningun conjunto de practicas de seguridad es infalible, Por lo tanto, las organizaciones deben de estar preparadas para contener el daño si se produce una violacion de la seguridad, esta se debe de mitigar rapidamente.

Aqui algunas medidas que deben de tomar las organizaciones cuando se identifica una violacion a la seguridad:

- **Comunicar el problema**
La comunicacion genera transpararencia, que es crucial para este tipo de situaciones.

Internamente, se debe de informar a todos los empleados y comunicar una llamada a la accion clara.

Externamente, todos los clientes deben ser informados a traves de una comunicacion directa y anuncios oficiales.

- **Ser sinceroy responsable**
Responda a la infraccion de manera honesta y genuina, asumiendo la responsabilidad cuando la organizacion tenga la culpa.

- **Proporcione los detalles**
Sea abierto y explique por que se produjo la infraccion y que informacion se vio comprometida. En general, se espera que las organizaciones se hagan cargo de los costos de los clientes asociados con los servicios de robo de indentidad requeridos como resultado de una violacion de seguridad.

- **Encuentre la causa**
Tome medidas para compreder que causo y facilito la infraccion. Esto puede implicar la contratacion de expertos forences para investigar y conocer los detalles.

- **Aplicar lecciones aprendidas**
Asegurese de que las lecciones aprendidas de las investigaciones forences se apliquen para evitar que se produzcan infracciones similares en el futuro.

- **Compuebre y vuelva a comprobar**
Los atacantes con frecuencia probaran a dejar una puerta trasera para facilitar las infracciones futuras. Para evitar que esto suceda, asegurece de que todos los sitemas esten limpios, no haya puertas traseras instaladasy nada mas se haya visto comprometido.

- **Eduque**
Sensibilice, capacite y eduque a los empleados, socios y clientes sobre como prevenir futuras infracciones.

## ¿Que es la gestion de riesgos?
La gestion de riesgos es el proceso formal de identificar y evaluar continuamente el riesgo en un esfuerzo por reducir el impacto de las amenazas y las vulnerabilidades. No puede eliminar el riesgo por completo pero puede determinar los niveles aceptables sopensando el impacto de una amenaza con el costo de implementar controles para mitigarla. *El costo de un control nunca debe de superar el valor del activo que esta protegido.*

- **Encuadre el riesgo**
Identifique las amenazas que aumentan el riesgo, productos, ataques, posibles fallos o interrupciones de los servicios, percepcion negativa de la reputacion de organizacion, responsable legal potencial o  perdida intelectual.

- **Evaluar el riesgo**
Determine la gravedad que representa cada amenaza. Por ejemplo, algunas amenzas pueden tener el potencial para paralizar toda una organizacion, mientras que otras amenazas pueden ser solo inconvenientes menores. El riesgo se puede priorizar evaluando el impacto finaciero (un analisis cuatitativo) o el impacto a escala e la operacion de una organizacion.

- **Responder al riego**
Desarrolle un plan de accion para reducir la exposicion general al riesgo de la organizacion, detallando donde se puede eliminar, mitigar, transferir o aceptar el riesgo.

- **Supervisar el riesgo**
Revise continuamente cualquier riesgo reducido mediante acciones de eliminacion, mitigacion o transferencia. Recuerde, no todos los riesgos se puede eliminar, por lo que debera monitorear de cerca cualquier amenaza que haya sido aceptada.