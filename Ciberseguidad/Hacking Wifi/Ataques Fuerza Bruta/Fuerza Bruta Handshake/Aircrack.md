Una vez capturado el [[Handshake]] podemos descubrir la contraseña con una ataque de fuera bruta, en el cual consisten en probar diferentes contraseñas que se almacenan en un text, a esto se le llama [[Diccionarios]] de contraseñas.

Uno puede generar estas contraseñas por medio de herramientas ya sea [[Conceptos/Hacking Wifi/Diccionarios/Herramientas/Cewl|Cewl]], [[Conceptos/Hacking Wifi/Diccionarios/Herramientas/Cupp|Cupp]], [[Conceptos/Hacking Wifi/Diccionarios/Herramientas/Crunch|Crunch]] etc. 

Para probar estas contraseñas se ejecuta lo siguiente:

	aircrack-ng -w diccContraseñas.txt CapturasAndHandShake.cap

-w *especifica el diccionario*