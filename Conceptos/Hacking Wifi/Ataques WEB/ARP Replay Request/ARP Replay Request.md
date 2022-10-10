# ARP Replay Request
Existen otro ataques para redes WEB como **FMS PTW que estos nesesitan recolipar un numero bastanta grande de tramas** para tener exito y estos se realizan de **forma pasiva, olfateando trafico inalambrico en el mismo canal del acceso point objetivo.**

El problema de esto es que en condiciones normales tendremos que esperar mucho tiempo recopilando pasivamente todos los paquetes nesesarios para el ataque y para acelerar el proceso lo ideal es inyectar tramas en la red para generar trafico en respuesta de modo que podamos recolectar los [[IVs]] nesesarios mas rapidamente.

Un tipo de trama adecuado para este proposito es la solicitud [[ARP]] por que el access point difunde cada vez con un nuevo IVs es decir con un nuevo vector de iniciacion.

Como usted no esta asociada al access point , si envia tramas directamente se descartaran y se envia una trama de autentificacion a su direccion MAC.

En cambios, se puede capturar solicitudes ARP de clientes asociados y restransmitirlas al accesspoint.

Esta tecnica se llama **ARP Replay Request**.