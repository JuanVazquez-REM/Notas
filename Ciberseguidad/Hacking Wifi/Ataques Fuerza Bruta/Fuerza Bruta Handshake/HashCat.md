# Fuerza bruta con HashCat

Al capturar el handshake con aircrack-ng podemos aplicar una fuerza bruta a este con [[Conceptos/Hacking Wifi/Herramientas/HashCat | HashCat]] 
para obtener el password del AC 

Primero debemos de pasar la captura ah un tipo de archivo legible para que lo comprensa hashcat

	aircrack-ng -j CapturaHCCAPX CapturaDeAuth-01.cap

Con el parametro *-j* y el nombre del nuevo archivo.

	hashcat -m 2500 -d 0 CapturaHCCAPX dicc.txt --outfile=password.txt --potile-disable

-m *Indicamos el tipo de hash, en este caso es un hash WPA*

``` bash
❯ hashcat --help | grep 2500
  25000 | SNMPv3 HMAC-MD5-96/HMAC-SHA1-96                     | Network Protocol
   2500 | WPA-EAPOL-PBKDF2                                    | Network Protocol
  12500 | RAR3-hp                                             | Archive
  22500 | MultiBit Classic .key (MD5)                         | Cryptocurrency Wallet
```

-d 0 *Indicamos el tipo dispositivo con el queremos trabajar (CPU)*
``` bash
- [ OpenCL Device Types ] -

  # | Device Type
 ===+=============
  1 | CPU
  2 | GPU
  3 | FPGA, DSP, Co-Processor
```

--outfile=password.txt *Archivo donde se guardara el resultado*
--potile-disable *Do not write potfile  

