Esto es de mucha utilidad cuanto lanzamos una shell remotamente hacia nuestra maquina, esto permite realizar ciertas acciones para tener mas desplazamiento sobre la shell.

Con esto obendremos una seudo consola

	$ script /dev/null -c bash

Aplicaremos un `crtl+z` para mandar el proceso en segundo plano

	$ stty raw -echo
	$ fg
	$ reset
	terminal type? xterm

Con esto ya tendremos nuestra consola interectiva, solo falta aplicar la misma resolucion que nuestra pantalla y determinar la *TERM* y *SHELL*.

	user@system$ export TERM=xterm  
	user@system$ export SHELL=bash

Para la resolucion tendremos que saber cuantas filas y columna tiene nuestra ventana.

	❯ stty -a
	 speed 38400 baud; rows 36; columns 146; line = 0;

Y aplicamos en la terminal victima.

	stty rows 36 columns 146