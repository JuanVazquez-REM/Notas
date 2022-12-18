Este control se encarga de administrar el intercambio de informacion entre el cliente y el AP, evitando colisiones entre las comunicación, este sistema de control mantiene tres tramas.

## Trama de solicitud de envio (RTS)
Ahora el cliente envía una trama RTS como primer antes de enviar tramas de datos.

## Trama de listo para enviar (CTS):
Un AP en respuesta de una trama RTS proporciona autorización al cliente para enviar tramas de datos. Ahora la trama CTS contribuye a la administración del control de colisiones al incluir un valor de tiempo, este valor de tiempo es el que baja las probabilidades de ocurra colisiones con otro cliente que desee hacer un RTS y CTS.

## Trama de acuse de recibo (ACK):
Después de recibir una trama de datos el receptor envía una trama ACK al emisor para saber si no se encuentran errores, si el emisor no recibe nada el un lapso reenviara la trama.

![[Pasted image 20221021133620.png]]
