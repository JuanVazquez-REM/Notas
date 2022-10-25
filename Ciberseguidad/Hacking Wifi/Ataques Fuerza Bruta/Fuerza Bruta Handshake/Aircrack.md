Una vez capturado el [[HandShake]] podemos descubir la contraseña con una ataque de fuera bruta, en el cual consisten en probar diferentes contraseñas que se almacenan en un txt, a esto se le llama [[Diccionarios]] de contraseñas.

Uno puede generar estas contraseñas por medio de herramientas ya sea [[Conceptos/Hacking Wifi/Diccionarios/Herramientas/Cewl]], [[Conceptos/Hacking Wifi/Diccionarios/Herramientas/Cupp]], [[Conceptos/Hacking Wifi/Diccionarios/Herramientas/Crunch]] etc. 

Para probar estas contraseñas se ejecuta lo siguiente:

	aircrack-ng -w diccContraseñas.txt CapturasAndHandShake.cap

-w *espesifica el diccionario*