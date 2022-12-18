Existen otro ataques para redes WEB como **FMS PTW que estos necesitan recopilar un numero bastante grande de tramas** para tener éxito y estos se realizan de **forma pasiva, olfateando trafico inalámbrico en el mismo canal del acceso point objetivo.**

El problema de esto es que en condiciones normales tendremos que esperar mucho tiempo recopilando pasivamente todos los paquetes necesarios para el ataque y para acelerar el proceso lo ideal es inyectar tramas en la red para generar trafico en respuesta de modo que podamos recolectar los [[IVs]] necesarios mas rápidamente.

Un tipo de trama adecuado para este propósito es la solicitud [[ARP]] por que el access point difunde cada vez con un nuevo IVs es decir con un nuevo vector de iniciación.

Como usted no esta asociada al access point , si envía tramas directamente se descartaran y se envía una trama de autentificación a su dirección MAC.

En cambios, se puede capturar solicitudes ARP de clientes asociados y retransmitirlas al access point.

Esta técnica se llama **ARP Replay Request**.