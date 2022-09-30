# Comandos

grep *filtra*
xargs *ejecuta algo con el output*
cat data.txt | wc -l *total de lineas*
cat data.txt | sort *ordenamiendo alfabetico*
cat data.txt | uniq -u *muestra las lineas unicas* alt wicth unique
sort data.txt uniq -u *muestra la unica linea unica* bandit 8

strings data.txt *muestra los caracteres imprimibles*
awk 'NR= =4'  *nos permite filtrar la linea de un output*k
awk 'NF{print \$NF}' *nos permite sacar el ultimo segundo parametro*
base64 *codifica mensajes*
base64 -d *decodifica*
tr *itera el output al igual que* sed
tr '  ' '\n' *los espacios remplazalos por un salto de linea, solo con caracteres*
sed 's/ /\n/g' *sed trabajamos en modo sustitucion* s *los espacios lo remplazas por saltos de linea, a todo el resultado* /g
head -n 1 *filtra la primera linea del output*
2>/dev/null *parametro de find permite que los errores se vallan a la ubicacion y solo me muestre los resultados enontrados*
xxd *to hexadecimal*
xxd -r *revertir hexadecimal*
7z *herramienta para descomprimir*
7z l *lista el contenido a descomprimir*
7z x *descomprimimos*
lsof -i:22 *se describe los procesos que se stan corriendo por un puerto*
xargs *trabaja con el output anterior*
pwdx {PID} *muestra desde donde se ejecuto el proceso*
echo /dev/tcp/127.0.0.1/30000 *verfica si el puerto 30000 del localhost esta abierto*
echo "cadena"  | nc localhost 30000 *enviamos una cadena a la ruta proporsionada* alternativa: nelnet
telnet localhost 30000 *nos conectamos al una ip y puerto*
openssl s_client -connect localhost 30000 *crea un comunicacion ssl con la ip y puerto proporcionada*
diff file.old file.new *lista las diferencias de un archivo a otro*
ps -eo command *ver comandos a nivel de sistema*
.bashrc *archivo que ejecuta despues de que se conecta uno al servidor*
bash *spawn una bash*
bash -p *atiende el uid*
nc -nlvp 2424 *se pone en escucha en el puerto indicado*
watch -n 1 ls -l *nos permite observar o ejecutar un comando cada lapso, en este caso ejecutara un ls -l cada segundo*
grep -v "wrong" *quita las lineas que coicidan con la palabra*
scp -p user@host:archivo . *copiamos un archivo a nuestra pc*
git log -p *lista los diferentes commits*
git branch -r *lista las branches*
git tag *vemos las tag*
git show secret *mostramos la tag*
mount /dev/sdb1 /usb  *montar usb*
umount /dev/sdb1 /usb  *desmontar usb*
trap ctrl_c INT *ejecuta cierta accion al presionar dicha tecla o combinacion de estas*
echo -n *evita los saltos de linea*
curl -s *s de silence lo que hace es quitar la tabla de carga*
less -S *muestra en formato de padding, tipo __more__*
grep "name" *para ubicarnos cerca de la linea*
grep "name" -A 2 *devuelve las 2 lineas por debajo de la buscada*
tail -n 1 *devuelve la ultima linea*
awk 'NF{print $NF}' *obtiene el ultimo argumento del output*
tr -d "$" *se elimina el caracter de todo el output*
awk "{print $2}" *saca el segundo argumento del output*
xprop WM_CLASS *visualiza la class_g *

Abrir una *bash* desde un more

	presionamos v
	:set  shell=/bin/bash
	:shell




144


nos permite rotar 13 posiciones
	abcdefgijklmnopqrstuvwxyz
	cat data.txt
		Gur cnffjbeq vf WIAOOSFzMjXXBC0KoSKBbJ8puQm5lIEi
	cat data.txt | tr '[G-ZA-Fg-za-f]' '[T-ZA-St-za-s]'
		The password is JVNBBFSmZwKKOP0XbFXOoW8chDz5yVRv
	



script bash
*recore las lineas de un archivo*

	#!/bin/bash
	
	contado=1
	
	while read line; do
		echo "Linea $contador: $line"
		let contador+=1
	done < /etc/passwd

Bash nos permite ejecutar una sentencia en una sola linea, ejemplo:

	contador=1; strings data.txt | grep "^=" | while read line; do echo "Linea $contador: $line"; let contador+=1; done | awk 'NR==4' | awk '$NF{print $NF}'




alex el capo podcast the wild project mirar ultimos 30 minutos

Reddit: aunixporn 



