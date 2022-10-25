# Tramas de control
Este control se encarga de administrar el intercambio de informacion entre el cliente y el AP, evitando colisiones entre las comunicacion, este sistema de control mantiene tres tramas.

## Trama de solicitud de envio (RTS)
Ahora el cliente envia una trama RTS como primer antes de enviar tramas de datos.

## Trama de listo para enviar (CTS):
Un AP en respuesta de una trama RTS proporciona autorizacion al cliente para enviar tramas de datos. Ahora la trama CTS contribuye a la administracion del control de coliciones al incluir un valor de tiempo, este valor de tiempo es el que baja las probalidades de ocurra coliciones con otro cliente que desee hacer un RTS y CTS.

## Trama de acuse de recibo (ACK):
Despues de recibir una trama de datos el receptor envia una trama ACK al emisor para saber si no se encuentran errores, si el emisor no recibe nada el un lapso reenviara la trama.

![[Pasted image 20221021133620.png]]
