Las [[Rainbow table]] son diccionarios decontraseñas con la diferencia que estan contienen la contraseña y el valor hash que representa, con el fin de que el proceso de el ataque de fuerza bruta sea mucho mas eficaz.

Con ayuda de la herramienta de airolib-ng de la familia de aircrack podemos construir una rainbow table.

	airolib-ng diccPre --import passwd dicc.txt
Creamos la tabla proporcionando el nombre que tendra esta e importando el diccionario en texto plano con el parametro *passwd*.

	echo "ESSID_victima" > essid.lst
Creamos un archivo con el bssid del AC que deseamos atacar.
-.essid.lst [[Airolib-ng#Archivo lst]]

	airolib-ng diccPre --import essid essid.lst
Importamos el essid al igual que las passwords

	airolib-ng diccPre --stats
Para saber si todo si importo correctamente, podemos observar las passwords y el essid asociado.
``` bash
There are 1 ESSIDs and 1 passwords in the database. 0 out of 1 possible combinations have been computed (0%).

ESSID	Priority	Done
BSSID_victima	64	0.0
```

	airolib-ng diccPre --clean all
Limpia la basura de la db.

	airolib-ng diccPre --batch
Comiensa a procesar las contrseñas para tener ya el diccionario preposesado 

	aircrack-ng -r diccPre CapturaDeAuth-01.cap
Realizamos el ataque de fuerza bruta con aircrack
-r *Indicamos que el diccionario es una db por lo tanto lo toma como una rainbow table*













### Notas
#### Archivo .lst
La extensión de archivo LST se utiliza para un archivo de lista de datos y se refiere a varios tipos de información que es utilizada por múltiples tipos de programas. Listas como estos pueden ser transferidos a cualquier programa de base de datos o aplicación de hoja de cálculo.