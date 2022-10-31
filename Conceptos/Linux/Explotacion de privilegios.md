Esto consiste en escalar de un usuario no privilegiado a uno privilegiado.

La siguiente informacion nos puede facilitar una escalda, pero exiten muchas mas.

- Exploits de kernel
- Vulnerabilidades de las aplicaciones
- Configuraciones incorrectas, como permisos en archivos debiles
- Abuso de sudo
- Abuso de setuid y setgid
- Trabajos cron
- Contraseñas deficientes


### Caso 1
**Configuraciones incorrectas**
Privilegios de escritura en /etc/passwd
Esto no puede llevar a root directamente

si nosotros vizualizamos