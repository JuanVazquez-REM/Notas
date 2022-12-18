## Seguridad basada en el comportamiento
Es una forma de detección de amenazas que implica capturar y analizar el flujo de comunicación entre un usuario en la red local y un destino local o remoto. Cualquier cambio en los patrones normales de comportamiento se considera anomalía y puede indicar un ataque.

Herramientas de detección basadas en el comportamiento.

- **Honeypot**
Esta herramienta atrae al atacante apelando su patrón predicho de comportamiento malicioso. Una vez que el atacante este dentro del Honeypot, el administrador de la red puede capturar, registrar y analizar su comportamiento para poder construir una mejor defensa.

- **Arquitectura de la solución Cisco Cyber Threat Defense**
Esta arquitectura es utilizada para la detección e indicadores basados en el comportamiento para proporcionar mayor visibilidad, contexto y control. El objetivo es saber quien esta llevando a cabo el ataque, que tipo de ataque están realizando y donde, cuando y como se esta produciendo el ataque. 

Esta arquitectura de seguridad utiliza muchas tecnologías de seguridad para lograr este objetivo.

### NetFlow
Esta tecnología se utiliza para recopilar informacion sobre los datos que fluyen a través de una red, *incluidos quienes y que dispositivos están en la red, cuando y como los usuarios y los dispositivos acceden a la red.*

NetFlow es un componente importante en el análisis de la detección basados en el comportamiento. *Los conmutadores, enrutadores y firewalls equipados con NetFlow pueden reportar informacion sobre la entrada , salida y viaje de datos a través de la red.*

Esta informacion se envía a los recopiladores de NetFlow que recopilan, *almacenan y analizan datos de NetFlow*, que se pueden utilizar para establecer comportamientos de referencia en mas de 90 atributos, como la dirección IP de origen y destino.

![[Pasted image 20221213203750.png]]


## Pruebas de penetración 
Estas pruebas son el acto de evaluar un sistema informático, una red o una organización en busca de vulnerabilidades de seguridad. Una prueba de penetración busca violar los sistemas, las personas, los procesos y el código para descubrir vulnerabilidades que podrían explotarse. Esta informacion se utiliza para mejorar las defensas del sistema y garantizar que puedan resistir mejor los ciberataques en el futuro.

***Procesos***

**1. Planificación**
En en esta etapa se recopila la mayor informacion posible sobre un sistema o red de destino, sus posibles vulnerabilidades y exploits para usarlo en su contra. Esto implica llevar a cabo un *reconocimiento pasivo o activo (hueva)* e investigación de vulnerabilidad. 

**2. Escaneo**
En esta etapa se lleva a cabo un reconocimiento activo para sondear un sistema o red objetivo e identificar posibles debilidades que, si se explotan, podrían dar acceso a un atacante. El reconocimiento activo puede incluir:

- Escaneo de puertos para identificar puntos de acceso potenciales en un sistema de destino.
- Análisis de vulnerabilidades para identificar posibles vulnerabilidades explotables de un objetivo en particular.
- Establecer una conexión activa con un destino (enumeración) para identificar la cuenta de usuario, la cuenta del sistema y cuenta del administrador.

**3. Obtener acceso**
Uno de los objetivos de las pruebas de penetración es obtener acceso al sistema destino y rastrear el trafico de la red, utilizando varios métodos para explotar el sistema, que incluyen:

- Lanzar exploits con carga útil en sistema (payload).
- Traspasar las barreras físicas a los activos.
- Ingeniería social.
- Explotar las vulnerabilidades del sitio web.
- Explotar vulnerabilidades o configuraciones incorrectas en el software y hardware.
- Violación de los controles de acceso.
- Descifrar Wi-Fi encriptado débil.

**4. Mantener el acceso**
La prueba mantendrá el acceso al objetivo para averiguar que datos del sistema son vulnerables a la explotación. *Es importante que permanezca sin ser detectados*, por lo general, utilizando puertas traseras, cabellos de Troya, Rootkit y otros canales encubiertos para ocultar su presencia.

Cuando esta infraestructura este en su lugar, la prueba procederá a recopilar los datos que se consideren valiosos.

**5. Análisis y reportes**
Proporcionar comentarios a través de un informe que recomienda actualizaciones de los productos, las políticas y la capacitación para mejorar la seguridad de la organización.


## Reducción del impacto
Si bien entendemos que las organizaciones son el mayor foco de ataques y estas hacen el mayor esfuerzo para prevenir estos ataques es inevitable ser atacados ya que ningún conjunto de practicas de seguridad es infalible, Por lo tanto, las organizaciones deben de estar preparadas para contener el daño si se produce una violación de la seguridad, esta se debe de mitigar rápidamente.

Aquí algunas medidas que deben de tomar las organizaciones cuando se identifica una violación a la seguridad:

- **Comunicar el problema**
La comunicación genera transparencia, que es crucial para este tipo de situaciones.

Internamente, se debe de informar a todos los empleados y comunicar una llamada a la acción clara.

Externamente, todos los clientes deben ser informados a través de una comunicación directa y anuncios oficiales.

- **Ser sincero responsable**
Responda a la infracción de manera honesta y genuina, asumiendo la responsabilidad cuando la organización tenga la culpa.

- **Proporcione los detalles**
Sea abierto y explique por que se produjo la infracción y que informacion se vio comprometida. En general, se espera que las organizaciones se hagan cargo de los costos de los clientes asociados con los servicios de robo de identidad requeridos como resultado de una violación de seguridad.

- **Encuentre la causa**
Tome medidas para comprender que causo y facilito la infracción. Esto puede implicar la contratación de expertos forences para investigar y conocer los detalles.

- **Aplicar lecciones aprendidas**
Asegúrese de que las lecciones aprendidas de las investigaciones forences se apliquen para evitar que se produzcan infracciones similares en el futuro.

- **Compruebe y vuelva a comprobar**
Los atacantes con frecuencia probaran a dejar una puerta trasera para facilitar las infracciones futuras. Para evitar que esto suceda, asegúrese de que todos los sistemas estén limpios, no haya puertas traseras instaladas nada mas se haya visto comprometido.

- **Eduque**
Sensibilice, capacite y eduque a los empleados, socios y clientes sobre como prevenir futuras infracciones.

## ¿Qué es la gestión de riesgos?
La gestión de riesgos es el proceso formal de identificar y evaluar continuamente el riesgo en un esfuerzo por reducir el impacto de las amenazas y las vulnerabilidades. No puede eliminar el riesgo por completo pero puede determinar los niveles aceptables sopesando el impacto de una amenaza con el costo de implementar controles para mitigarla. *El costo de un control nunca debe de superar el valor del activo que esta protegido.*

- **Encuadre el riesgo**
Identifique las amenazas que aumentan el riesgo, productos, ataques, posibles fallos o interrupciones de los servicios, percepción negativa de la reputación de organización, responsable legal potencial o  perdida intelectual.

- **Evaluar el riesgo**
Determine la gravedad que representa cada amenaza. Por ejemplo, algunas amenazas pueden tener el potencial para paralizar toda una organización, mientras que otras amenazas pueden ser solo inconvenientes menores. El riesgo se puede priorizar evaluando el impacto financiero (un análisis cuantitativo) o el impacto a escala e la operación de una organización.

- **Responder al riego**
Desarrolle un plan de acción para reducir la exposición general al riesgo de la organización, detallando donde se puede eliminar, mitigar, transferir o aceptar el riesgo.

- **Supervisar el riesgo**
Revise continuamente cualquier riesgo reducido mediante acciones de eliminación, mitigación o transferencia. Recuerde, no todos los riesgos se puede eliminar, por lo que deberá monitorear de cerca cualquier amenaza que haya sido aceptada.