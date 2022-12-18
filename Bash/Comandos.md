grep *filtra*
xargs *ejecuta algo con el output*
cat data.txt | wc -l *total de líneas*
cat data.txt | sort *ordenamiento alfabético*
cat data.txt | uniq -u *muestra las líneas únicas* alt wicth unique
sort data.txt uniq -u *muestra la única linea, única* bandit 8

strings data.txt *muestra los caracteres imprimibles*
awk 'NR= =4'  *nos permite filtrar la linea de un output*k
awk 'NF{print \$NF}' *nos permite sacar el ultimo segundo parámetro*
base64 *codifica mensajes*
base64 -d *decodifica*
tr *itera el output al igual que* sed
tr '  ' '\n' *los espacios remplázalos por un salto de linea, solo con caracteres*
sed 's/ /\n/g' *sed trabajamos en modo sustitución* s *los espacios lo remplazas por saltos de linea, a todo el resultado* /g
head -n 1 *filtra la primera linea del output*
2>/dev/null *parámetro de find permite que los errores se vallan a la ubicación y solo me muestre los resultados encontrados*
xxd *to hexadecimal*
xxd -r *revertir hexadecimal*
7z *herramienta para descomprimir*
7z l *lista el contenido a descomprimir*
7z x *descomprimimos*
lsof -i:22 *se describe los procesos que están corriendo por un puerto*
xargs *trabaja con el output anterior*
pwdx {PID} *muestra desde donde se ejecuto el proceso*
echo /dev/tcp/127.0.0.1/30000 *verfica si el puerto 30000 del localhost esta abierto*
echo "cadena"  | nc localhost 30000 *enviamos una cadena a la ruta proporcionada* alternativa: telnet
telnet localhost 30000 *nos conectamos al una ip y puerto*
openssl s_client -connect localhost 30000 *crea un comunicación SSL con la ip y puerto proporcionada*
diff file.old file.new *lista las diferencias de un archivo a otro*
ps -eo command *ver comandos a nivel de sistema*
.bashrc *archivo que ejecuta después de que se conecta uno al servidor*
bash *spawn una bash*
bash -p *atiende el uid*
nc -nlvp 2424 *se pone en escucha en el puerto indicado*
watch -n 1 ls -l *nos permite observar o ejecutar un comando cada lapso, en este caso ejecutara un ls -l cada segundo*

grep -v "wrong" *quita las líneas que coincidan con la palabra*
scp -p user@host:archivo . *copiamos un archivo a nuestra pc*
git log -p *lista los diferentes commits*
git branch -r *lista las branches*
git tag *vemos las tag*
git show secret *mostramos la tag*
mount /dev/sdb1 /usb  *montar usb*
umount /dev/sdb1 /usb  *desmontar usb*
trap ctrl_c INT *ejecuta cierta acción al presionar dicha tecla o combinación de estas*
echo -n *evita los saltos de linea*
curl -s *s de silence lo que hace es quitar la tabla de carga*
less -S *muestra en formato de padding, tipo __more__*
grep "name" *para ubicarnos cerca de la linea*
grep "name" -A 2 *devuelve las 2 líneas por debajo de la buscada*
tail -n 1 *devuelve la ultima linea*
awk 'NF{print \$NF}' *obtiene el ultimo argumento del output*
tr -d "\$" *se elimina el carácter de todo el output*
awk "{print \$2}" *saca el segundo argumento del output*
xprop WM_CLASS *visualiza la class_g*
grep "Entradas" -A 100 *hace el filtro y hace un output de 100 líneas hacia bajo* -B *líneas hacia arriba*
head -n -2 *quita las 2 ultimas líneas*
grep  -n "user" *retorna la linea donde se encontró el filtro*
awk '{print \$1}' FS=":" *fíltrame el primer argumento donde el delimitador sea :*
sed "\${line_null}s/\$/0/" -i result.tmp *indico que quiero hacer una sustitución en una linea especifica, en un archivo existe*
grep -r -i *-r Busca en la ubicación actual de forma recursiva, -i quita el case insensitive*
netstat -ln *Lista los puertos abiertos en nuestro equipo*
which nano *Saber done se ubica executable nano*
grep -oP *Filtro por expresiones regulares*
timeout 1 bash -c "echo ' ' >/dev/tcp/10.10.10.11/80" *El timeout indica que cancelara el proceso en 1 segundo*
updatedb *Es una forma de sincronizar todos los archivos a nivel de sistema*
grep -oP '".\*?"' *Filtra la informacion que este dentro de " "* .\*? *esto significa data*
xxs -ps -r *Convierte hexadecimal o string*
find
/etc/hosts *Virtual hosting*
awk '{print $1 "\_\_" $2 "  " $3 }'  *podemos acomodar los argumentos*
awk 'NR%2' *me da el output cada 2 líneas*
awk 'NR%2{printf "%s ",$0;next;}1'  *sobre este output muéstrame un string que es la linea siguiente, 1 para que sea una linea por debajo*
du -hc file *ver peso del file*
upx file *comprime el archivo, lo hacer menos pesado*
ps -eo command *observas todos los comandos que se están ejecutando actualmente*
python -m SimpleHTTPServer 80 *Monta un servidor http con Python*
php -S 0.0.0.0:80 *Monta un servidor http*
shred -zun 10 -v file *Eliminar archivo y las tablas de índices, haciendo mas difícil su recuperación*
/proc/net/tcp *Se registra los puertos abiertos ya sea internos como externos*
grep -oP '\w{1,10}:.\*' *Filtro por expresión regulares \w "Empieza por", {1,10} "1 hasta 10 caracteres" , :.\* "seguido de : muéstrame todo lo que le sigue"* 
df -h *ver el almacenamiento*

Se sabe que un archivo de php no se puede leer solo se interpreta, pero existe una manera de burlar esto con los wrappers y un LFI, que consiste en codificar el archivo en base64.

	php://filter/convert.base64-encode/resource=archivo.php

Nos permite rotar 13 posiciones
	abcdefgijklmnopqrstuvwxyz
	cat data.txt
		Gur cnffjbeq vf WIAOOSFzMjXXBC0KoSKBbJ8puQm5lIEi
	cat data.txt | tr '[G-ZA-Fg-za-f]' '[T-ZA-St-za-s]'
		The password is JVNBBFSmZwKKOP0XbFXOoW8chDz5yVRv
	

Bash nos permite ejecutar una sentencia en una sola linea, ejemplo:

	contador=1; strings data.txt | grep "^=" | while read line; do echo "Linea $contador: $line"; let contador+=1; done | awk 'NR==4' | awk '$NF{print $NF}'



