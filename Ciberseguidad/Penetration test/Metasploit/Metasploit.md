# Metasploit
Metasploit framework es una herramienta desarrollada en Perl y Ruby en su mayor parte, que está **enfocada a auditores de seguridad y equipos Red Team y Blue Team**.

**Es una herramienta muy completa que tiene muchísimos exploits**, que son vulnerabilidades conocidas, en las cuales tienen también unos módulos, llamados [[Payload]], que son los códigos que explotan estas vulnerabilidades.

También **dispone de otros tipo de módulos**, por ejemplo, los encoders, que son una especie de códigos de cifrado para evasión de antivirus o sistemas de seguridad perimetral.

	msfconsole
Ejecuta el framework de mestasploit

	searchsploit ProFTP 1.3.3.c
Lo que hace es buscar meta sploit que sean vulnerables para la version del servicio.

-ProFTP 1.3.3.c *es la version del servicio donde queremos buscar vulnerabilidades*

	use xploit/unix/ftp/proftpd_133c_backdoor
Usa el metasploit que se esta en la siguiente ruta

	show options
Muetra los datos que debemos de introducir en el sploit que queremos utilizar

	set RHOSTS 192.168.1.68
Esto sirve para setear valores que el splot nos pide

-RHOSTS *Es el nombre del parametro que es requerido por el sploit*
-192.168.1.68 *Es el valor el valor que le damos al parametro RHOSTS*





	