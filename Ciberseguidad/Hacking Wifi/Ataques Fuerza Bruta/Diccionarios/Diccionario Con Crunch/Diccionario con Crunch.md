# Creaccion de diccionario con crunch
Para la creacion de un diccionario se utilizara la herramienta de [[Crunch]] donde para crear un diccionario se hara lo siguiente.

En la siguiente ubicacion se encuentran los diferentes conjuntos de caracteres con los que podemos formular nuestros diccionarios.

	cd /usr/share/crunch/charset.lst

Crunch utiliza un conjunto de caracteres por defecto que serian los *lalpha* que contienen los siguientes caracteres, podemos selecionar los diferentes conjutos de caracteres que Crunch nos ofrece.

	lalpha = [abcdefghijklmnopqrstuvwxyz]

	crunch 1 8 -o pruebaDic.txt
Crear diccionario con los diferentes parametros.

-1 *Minimo de longitud de nuestras contraseñas*
-8 *Maximo de longitud de nuestras contraseñas*
-o *Especifica el archivo de salida por ejemplo pruebaDic.txt*
-pruebaDic.txt *pruebaDic.txt es el nombre nuestro diccionario*


Puedes encontrar mas informacion aqui:
	https://www.hackingarticles.in/comprehensive-guide-on-crunch-tool/
	https://null-byte.wonderhowto.com/how-to/tutorial-create-wordlists-with-crunch-0165931/

