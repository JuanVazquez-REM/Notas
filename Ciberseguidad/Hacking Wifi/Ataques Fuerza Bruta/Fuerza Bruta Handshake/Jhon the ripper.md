# Fuerza bruta con Jhon The Ripper

Una vez que se captura el [[HandShake]] podemos desifrar con la herramienta [[Ciberseguidad/Conceptos/Hacking Wifi/Herramientas/Jhon The Ripper | Jhon The Ripper]] lo que se hara es verificar el hash obtenido por el handshake con algun diccionario de contraseñas.

Primero debemos de pasar la captura obtenida es decir *CapturaDeAuth-01.cap* a un archivo *hashcat (HCCAP)* con aircrack-ng 

	aircrack-ng -J CapturaHCCAP CapturaDeAuth-01.cap
-j *nombre del archivo.hccap*

	 hccap2jhon CapturaHCCAP > hash.txt
Le pasamos la captura hccap a jhon para que la pase a formato legible, es decir hash.txt

	jhon -w=dicc.txt hash.txt
Ahora pasamremos el diccionario a jhon con el parametro *-w=dicc.txt* justo con el hash, esto puede decirnos si se encontro la contraseña.

	jhon -show hash.txt
Si se encontro una contraseña valida podemos verla con *-show* y proporcionar el hash

