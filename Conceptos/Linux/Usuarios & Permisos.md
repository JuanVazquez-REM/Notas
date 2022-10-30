# Usuarios
Como bien sabemos los usaurios del sistema se encuentran en `> /etc/passwd` cada uno de estos usuarios tiene una shell, podemos ver las shells registradas en el sistema.

	> /etc/shells

Si deseamos filtrar los usuarios, podemos aplicar un filtro por quien utiliza una *shell* ya que estan siempre terminan en *sh*

	




# Permisos
**-rwsr-x---**
La **s** en rws significa setuid, lo que significa establecer ID de usuario. Este es un bit de permiso especial que permite que el programa, cuando lo ejecuta cualquier usuario, se ejecute con el UID efectivo del propietario

*Nota:*
Este bit de permiso es un riesgo para la seguridad y solo debe aplicarse cuando sea absolutamente necesario.