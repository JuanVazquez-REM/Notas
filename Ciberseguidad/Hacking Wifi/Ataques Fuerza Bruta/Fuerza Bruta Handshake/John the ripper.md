Una vez que se captura el [[HandShake]] podemos descifrar con la herramienta [[Conceptos/Hacking Wifi/Herramientas/Jhon The Ripper |John The Ripper]] lo que se hará es verificar el hash obtenido por el handshake con algún diccionario de contraseñas.

Primero debemos de pasar la captura obtenida es decir *CapturaDeAuth-01.cap* a un archivo *hashcat (HCCAP)* con aircrack-ng 

	aircrack-ng -J CapturaHCCAP CapturaDeAuth-01.cap
-j *nombre del archivo.hccap*

	 hccap2jhon CapturaHCCAP > hash.txt
Le pasamos la captura hccap a Jhon para que la pase a formato legible, es decir hash.txt

	jhon -w=dicc.txt hash.txt
Ahora pasaremos el diccionario a Jhon con el parámetro *-w=dicc.txt* justo con el hash, esto puede decirnos si se encontró la contraseña.

	jhon -show hash.txt
Si se encontró una contraseña valida podemos verla con *-show* y proporcionar el hash

