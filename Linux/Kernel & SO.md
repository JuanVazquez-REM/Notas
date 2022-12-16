Una vez que conocemos el mundo de linux nos damos cuentas que existen una infindad de *distribuciones* no sistemas operativos ya que estos se extendien del SO de codigo abierto, Linux. Es por esto que comparten el mismo nucleo o como se le conoce el *kernel de linux*. 

Linux es un sistema operativo, *aunque nadie lo utiliza como tal*, *si no que se recurre a las versiones o distribuciones* que crea una organizacion o la propia comunidad, con el fin de se mucho mas util y sencillo de usar.


## ¿Que es el kernel?
Esto es la parte fundamental de un sistema operativo ya que este software se encarga de conceder el acceso al hardware de forma segura para el todo el software que lo solicita.

Todos los sistemas operativos tiene un kernel y por supuesto windows lo tiene, aunque el mas conocido es el kernel de linux. 

**Dato:** las ultimas actualizaciones de windows integran el kernel de linux (acelera el comportamiento de sistema de ficheros, ademas agrega mejoras para los desarrolladores).

*Este software se ejecuta de manera privilegiada con acceso especial a los recursos del sistema* ya que es el que se encarga de gestionar en caso de que un software lo nesesite como se habia mencionado anteriormente, *ahora los recursos no son ilimitados asi que las tareas que se le asignas se van ejecutando segun la prioridad e importancia de estas*.
![[Pasted image 20221215003137.png]]

## ¿Para que sirve?
Este se encarga de gestionar todo el hardware para ser utilizado por el software, es decir que *gestiona la memoria del sistema, tiempos del procesos, controlar llamadas del sistema, conexiones entre procesos, conceder acceso a los perfirericos, etc, de manera eficaz y ordenada.*

Es decir que tiene control total del hardware de nuestro equipo, asi que se ocurre un error en algun proceso en el *espacio del usuario* el SO seguira funcionando e incluso puede intentar recurar el sistema al tener el control total, sin embargo si ocurre un error dentro del *espacio del kernel* todo el sistema deja de funcionar y puede provocar como en el caso de windows como una <*Pantalla azul :(*> o como en linux con un mensaje de <*Kernel Panic*>.


## ¿Que hace el kernel de linux?
Como ya se hablo anteriormente la funcion de un kernel en un SO es fundamental es por eso que tiene muchas funciones, pero en este apartado hablaremos de cuatro trabajos englobando sus subtareas.

**1. Gestion de memoria**
Realiza un seguimiento de cuanta memoria se utiliza para almacenar que y donde.

**2. Gestion de pocesos**
Determina que procesos pueden utilizar la unidad central de procesamiento (CPU), cuando y durante cuanto tiempo.

**3. Controladore de dispositivo**
Actua como mediador/interprete entre el hardware y los procesos.

**4. Llamadas al sistema y seguridad**
Recibit solicitudes de servicio de los procesos.

El kernel si se implenta correctamente, este es invisible para el usuario, ya que este trabaja en su *propio mundo conocido con el el espacio de kernel*, que es donde hace toda su gestion del hardware al software. Lo que el usuario ve, como las aplicacione, archivos, etc se le *conoce como espacio de usuario*. Estas aplicaciones interactuan con el kernel a traves de la interfaz de una llamada al sistema (SCI).


## ¿Que es un SO?
En sistema operativo es termino para lo programas (software del sistema) que hace posible el funcionamiento de un sistema, este controla y supervisa la interaccion de los componentes de hardware, esto te suena similar? 

Pues bien las partes principales de un SO son

1. Nucleo (kernel)
2. El traductor de comando (shell)
3. Sistemas de archivos

Y aqui un esquema de como se junta todo.

![[Pasted image 20221215111046.png]]
## Distribusiones
Bueno una vez entendemos lo que hace un kernel pasemos al kernel de linux original (vanilla) en el cual la comunidad o organizacion mejora o modifica este kernel para compilar una version personalizada de este.

Y por lo tanto hablamos que el kernel de linux es de codigo abierto pues existen multiples distro enfocadas a un perfil de usuario.


## Tipos de kernel
Una vez sabemos que es y que hace un kernel, entederemos que existen tipos, pero esto cumplen su misma funcion.


**MicroKernel**
Este suele tener un codigo pequeño y hace lo posible para que la comutadora funcione correctamente y la demas tareas son cubiertas por servicios que se van pasando por el kernel, la ventaja de esta arquitectura es que si falla algun servicio seguira funcionado el kernel y el error quedara aislada de esta

**Kernel monolitico**
Ahora dado que el microkernel usa servicios externos al kernel, este tipo hace que los servicios formen parte del mismo kernel, la ventaja de esta arquitectura es que no se pierde tanto tiempo al estarse comunicando con servicios, de esta forma el tiempo del sistema se aprovecha mejor.

El tipo de kernel de *Linux* es *monolitico* mientras tanto los kernels de *Windows* o *macOS* son hibridos, ya que algunos de las *tareas son manejadas como microkernel pero las tarea de mayor importancia de manejan con monolitico.*

