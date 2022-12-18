Es una aplicación de Ruby que rastrea una determinada URL a una profundidad especificada, siguiendo opcionalmente enlaces externos, y devuelve una lista de palabras que pueden ser usadas para crackers de contraseñas.

## Parámetros
-w file.txt *Guarda el output*
-with-number *Busca números dentro de la pagina*
-m 5 *Nos permite seleccionar un mínimo de caracteres para buscar, por defecto son 3*
-o *Indica búsqueda en las urls relacionas a la url principal*
-e *Búsqueda de emails*
--email_file \<file\> *Exporta un archivo de email, con un formato adecuado*