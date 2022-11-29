Esto consiste en escalar de un usuario no privilegiado a uno privilegiado.

La siguiente informacion nos puede facilitar una escalda, pero exiten muchas mas.

- Exploits de kernel
- Vulnerabilidades de las aplicaciones
- Configuraciones incorrectas, como permisos en archivos debiles
- Abuso de sudo
- Abuso de setuid y setgid
- Trabajos cron
- Contraseñas deficientes


### Abuso de permisos
**Configuraciones incorrectas**
Privilegios de escritura en */etc/passwd*

	-rw-r--rw- 1 root root 3098 oct 30 07:14 /etc/passwd

Si nosotros vizualizamos el */etc/passwd* podemos ver los usuarios y una estructura

	root:x:0:0:root:/root:/usr/bin/zsh
*root:x:* esto es lo interesante, la primera parte corresponde al user la segunda a la contraseña, pero todas las contraseñas de los usuarios estan en */etc/shadow*

	 root:$y$j4T$irDX/b1D.xsGnAjgwXqjN0$SUhJ7c+masHash:19295:0:99999:7:::
Estas se guardan con un cifrado SH512 y por obvias razones no muestra el hash donde se encuentra la *x*.

Ahora cuando nosotros aplicamos un *su* inmediatemente linux busca este usuario en */etc/passwd* y despues compara la contrasela ingresada(Hasheada) con el hash de */etc/shadow*.

La idean es colocar un contraseña cifrada en */etc/password* en *root:x:* para que cuando el apliquemos un *su*, busque el usuario en */etc/passwd* y que no le de tiempo en ir hasta */etc/shadow* y comparar el hash real y compare el que ingresamos.

	#Crear passwd con cifrado MD5(unix) 
	openssl passwd
	#file /etc/passwd
	root:$1$Oj5vDRtl$gLDk3yZydofZs87dn2wR20:0:0:root:/root:/usr/bin/zsh
	su root

*Nota:* En caso de tener permiso de escritura en  */etc/shadow* podria hacer lo mismo, crear una contraseña hasheada y editar el usuario.


## Abuso de sudo
Otro escalada seria teniendo un permiso sudo en alguna herramienta como *zip*, ya que con gtfobins podemos encontrar la escalada por *zip*.

	sudo zip file_name /etc/hosts -T -TT 'sh #'

## Abuso de suid
Este tipo de permiso especial nos algo como el usuario propietario de forma temporal, supongamos que el el *timeout* cuenta con permisos suid por parte del usuario *root*, asi que buscamos en *gtfobins*.

	timeout 7d /bin/sh -p


## Abuso de kernel
Esto se abusa de vulnerabilidades que tiene el propio kernel el cual muy probablemente este desactualizado para que tenga este tipo de vulnerabilidades.

El exploit 40839 de *exploit-db*

Contiene un script en *c* el cual con privilegios de escritura va a crear un usuario nuevo y su contrseña en el */etc/passwd*

