Supongamos que tenemos una captura del trafico de un AP y *registramos un handshake* y deseamos ver los paquetes *http* y realizamos un filtro a la captura con [[Tshark]].

	tshark -r CapturaDeAuth.cap -Y "http" 2>/dev/null

Y vemos que no hay ningun resultado. *Esto pasa por que todo el trafico interno de la red esta encriptado con la password de AP*.

Ahora si disponemos de la password podemos desencriptar el trafico con la herramienta airdecap-ng.

	airdecap-ng -e "essid_victima" -p password123 CapturaTrafico-01.cap

Veremos un resumen de los paquetes con una lista de los paquetes *encriptados y desencriptados* esto nos debe de generar un archivo replica de *CapturaTrafico-01.cap* con un *-dec*.

``` bash
Total number of stations seen            8
Total number of packets read         26443
Total number of WEP data packets         0
Total number of WPA data packets      7240
Number of plaintext data packets         0
Number of decrypted WEP  packets         0
Number of corrupted WEP  packets         0
Number of decrypted WPA  packets      7147
Number of bad TKIP (WPA) packets         0
Number of bad CCMP (WPA) packets         0
```

Ahora con el archivo *CapturaTrafico-01-dec.cap* podemo inspecionar los paquenes *dns*, *http* y posiblemente la data enviada por este, *recordemos que si se envio data por https* no podremos vizualizarla con este decifrado. 

