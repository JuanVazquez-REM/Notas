WireShark  al igual que [[Tshark]], es una herramienta para el analisis de la red, provando si existe una actidad sospechosa, latencia o fallos en la red. Tambien permite importar capturas de red para su analisis.


## Uso

### Filters
wlan.fc.type_subtype=\=28 *Filtra los paquetes CTS*
wlan.fc.type_subtype=\=4 *Filtra por paquetes [[Tramas y Paquetes#Probe Resquest | Probe Request]]*
wlan.fc.type_subtype=\=5 *Filtra por paquetes [[Tramas y Paquetes#Probe Response| Probe Response]]*
wlan.fc.type_subtype=\=1 *Filtra por paquetes [[Tramas y Paquetes#Association Response| Association Response ]]*
wlan.fc.type_subtype=\=1 *Filtra por paquetes [[Tramas y Paquetes#Beacon Frames| Beacon Frame ]]*
wlan.fc.type_subtype=\=11 *Filtra por paquetes [[Tramas y Paquetes#Authentication|  Authentication]]*
wlan.fc.type_subtype=\=12 *Filtra por paquetes [[Tramas y Paquetes#DeAuthentication|  DeAuthentication]]*
wlan.fc.type_subtype=\=10 *Filtra por paquetes [[Tramas y Paquetes#Dissasociation Frame|  Dissasociation Frame]]*



 