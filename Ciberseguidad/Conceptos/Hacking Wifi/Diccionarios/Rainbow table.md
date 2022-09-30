# Rainbow table
Un ataque de tabla arco iris es un método de descifrado de contraseñas que utiliza una tabla especial (una "tabla arco iris") para descifrar los hashes de contraseña en una base de datos.

La tabla arco iris en sí se refiere a una tabla precalculada que contiene el valor hash de contraseña para cada carácter de texto sin formato utilizado durante el proceso de autenticación.


## Cómo protegerse contra un ataque de mesa arco iris

Protegerse de los ataques de la mesa del arco iris es relativamente sencillo si sigue estas pautas:

-   **Eliminar contraseñas**: La ÚNICA forma de garantizar la prevención de ataques basados en contraseñas es mediante la eliminación de contraseñas. Sin una lista de hashes de contraseña para robar, no hay forma de ejecutar un ataque de tabla arcoíris. Obtenga más información sobre [la autenticación sin contraseña](https://www.beyondidentity.com/resources/passwordless-authentication "Passwordless Authentication: What It Is and How It Works") hoy mismo y mantenga seguras sus aplicaciones más críticas.
-   **Use salting**: Las contraseñas hash nunca deben almacenarse sin salting. Esto hace que la contraseña sea más difícil de descifrar. Sin embargo, recomendamos eliminar la contraseña alfanumérica por completo.
-   **Usar datos biométricos**: El uso de un método biométrico de autenticación hace que sea difícil, si no imposible, que un atacante use un ataque de mesa arco iris de manera efectiva. Los ataques de tabla Rainbow no funcionarán contra contraseñas biométricas.
-   **Supervise sus servidores**: La mayoría de los programas de seguridad de servidores modernos monitorean los intentos de acceder a información confidencial y pueden actuar automáticamente para mitigar y atrapar a los intrusos antes de que puedan encontrar la base de datos de contraseñas.
-   **No utilice algoritmos hash obsoletos**: los hackers buscan aplicaciones y servidores utilizando algoritmos hash de contraseña obsoletos MD5 y SHA1. Si la aplicación utiliza cualquiera de los algoritmos, el riesgo de ataques a la tabla arco iris aumenta sustancialmente.
