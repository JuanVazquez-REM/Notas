Para la creación de un diccionario se utilizara la herramienta de [[[Conceptos/Hacking Wifi/Diccionarios/Herramientas/Crunch]]donde para crear un diccionario se hará lo siguiente.

En la siguiente ubicación se encuentran los diferentes conjuntos de caracteres con los que podemos formular nuestros diccionarios.

	cd /usr/share/crunch/charset.lst

Crunch utiliza un conjunto de caracteres por defecto que serian los *Alpha* que contienen los siguientes caracteres, podemos seleccionar los diferentes conjuntos de caracteres que Crunch nos ofrece.

	lalpha = [abcdefghijklmnopqrstuvwxyz]

	crunch 1 8 -o pruebaDic.txt
Crear diccionario con los diferentes parámetros.

-1 *Mínimo de longitud de nuestras contraseñas*
-8 *Máximo de longitud de nuestras contraseñas*
-o *Especifica el archivo de salida por ejemplo pruebaDic.txt*
-pruebaDic.txt *pruebaDic.txt es el nombre nuestro diccionario*


Puedes encontrar mas informacion aquí:
	https://www.hackingarticles.in/comprehensive-guide-on-crunch-tool/
	https://null-byte.wonderhowto.com/how-to/tutorial-create-wordlists-with-crunch-0165931/

