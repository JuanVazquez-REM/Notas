Este creador de directorios es particular, ya que [[Conceptos/Hacking Wifi/Diccionarios/Herramientas/Cewl]] esta hecho para crear diccionarios extrayendo informacion de una pagina web.

Por ejemplo le proporcionamos la pagina de facebook.com y lo que va hacer es buscar todas la palabras de facebook.com y después va a formar un diccionario con todas la palabras que pudo recolectar, a se le llama *ataque spider*.

	cewl -e -w diccionarioCewl https://juankaenel.com -v
Crea un diccionario en base a las palabras de la pagina

-e *Incluye los emails*
-w *Especifico el nombre del archivo donde se guardaran las posibles contraseñas*
-https://juankaenel.com *Es la url de la pagina de donde sacara las palabras*

	grep @ diccionarioCewl
Realiza una búsqueda del carácter, en un determinado archivo

-@ *Carácter que deseamos buscar*
-diccionarioCewl *Archivo donde se realizara la búsqueda*
