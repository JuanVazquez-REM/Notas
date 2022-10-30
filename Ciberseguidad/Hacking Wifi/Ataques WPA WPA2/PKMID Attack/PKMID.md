En pocos palabras este ataque no requiere de usuarios conectados a la red, por lo tanto no requiere que se capture un handshake.

Este consiste en la comunicacion directa con el router, en su lugar extrae [RSNIE](https://www.tech-faq.com/rsn-robust-secure-network.html) solo un frame de [EAPOL](https://es.wikipedia.org/wiki/Extensible_Authentication_Protocol)

Ahora para obtener lo que nos interesa es nesesario hacer una serie de calculos y esto requiere de una fuerza de computo, esto se reduce gracias al **hash-mode 16801** por lo tanto hace mas facil capturar el PMK.

Con este obtendremos el hash y podemos a proceder con el crackeo, con lo metodos que ya conocemos para romper un hash.
[Mas informacion](https://blog.elhacker.net/2018/08/nuevo-metodo-de-ataque-en-redes-wifi-wpa-wpa2-psk-PMKID.html#:~:text=Pairwise%20Master%20Key%20Identifier%20(PMKID,direcci%C3%B3n%20MAC%20de%20la%20estaci%C3%B3n.)

