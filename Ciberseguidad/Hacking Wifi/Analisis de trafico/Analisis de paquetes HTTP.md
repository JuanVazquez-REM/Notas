En este caso veremos como es de facil saber la data que es enviada a travez de metodos POST por paginas que no cuentran con un cifrado SSL, es decir paginas HTTP.

Por lo tanto nos pondremos en escucha de paquetes con [[WireShark]] en nuestra propia interfaz de red, despues enviamos una peticion POST.

![[login-http.jpeg]]

Y solo sera cuestion de filtrar los paquetes por http buscamos en concreto una peticion por el metodo POST que corresponda a la que buscamos y listo observamos la data enviada.

![[package-http-post.jpeg]]