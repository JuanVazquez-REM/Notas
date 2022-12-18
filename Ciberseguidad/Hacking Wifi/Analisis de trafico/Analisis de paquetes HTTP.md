En este caso veremos como es de fácil saber la data que es enviada a través de métodos POST por paginas que no cuentan con un cifrado SSL, es decir paginas HTTP.

Por lo tanto nos pondremos en escucha de paquetes con [[WireShark]] en nuestra propia interfaz de red, después enviamos una petición POST.

![[login-http.jpeg]]

Y solo será cuestión de filtrar los paquetes por http buscamos en concreto una petición por el método POST que corresponda a la que buscamos y listo observamos la data enviada.

![[package-http-post.jpeg]]