# DeCompressor
Desafio bandit12

La contraseña esta en un archivo que ah sido comprimido consecutivamente, se tiene que descomprimir cada uno de estos hasta llegar al archivo.

se puede hacer manual pero es mejor hacer un script para realizar un bucle.

Obtener el nombre del archivo a descomprimir. 

	┌──(juanvazquez㉿kali)-[~]
	└─$ 7z l data.gzip 
	
	7-Zip [64] 16.02 : Copyright (c) 1999-2016 Igor Pavlov : 2016-05-21
	p7zip Version 16.02 (locale=es_MX.UTF-8,Utf16=on,HugeFiles=on,64 bits,2 CPUs AMD A9-9410 RADEON R5, 5 COMPUTE CORES 2C+3G    (670F00),ASM,AES-NI)
	
	Scanning the drive for archives:
	1 file, 608 bytes (1 KiB)
	
	Listing archive: data.gzip
	
	--
	Path = data.gzip
	Type = gzip
	Headers Size = 20
	
	   Date      Time    Attr         Size   Compressed  Name
	------------------- ----- ------------ ------------  ------------------------
	2022-09-01 01:30:09 .....          575          608  data2.bin
	------------------- ----- ------------ ------------  ------------------------
	2022-09-01 01:30:09                575          608  1 files

grep "name" *para ubicarnos cerca de la linea*
grep "name" -A 2 *devuelve las 2 lineas por debajo de la buscada*
tail -n 1 *devuelve la ultima linea*
awk 'NF{print $NF}' *obtiene el ultimo argumento del output*

	┌──(juanvazquez㉿kali)-[~]
	└─$ 7z l data.gzip | grep "Name" -A 2 | tail -n 1 | awk 'NF{print $NF}'
	data2.bin

Automatizar con script

```bash
!/bin/bash

name_decompressed=$(7z l data.gzip | grep "Name" -A 2 | tail -n 1 | >
7z x data.gzip > /dev/null 2>&1

while true; do
		7z l $name_decompressed > /dev/null 2>&1

		if [ "$(echo $?)" == "0" ]; then
				decompressed_next=$(7z l $name_decompressed | grep ">
				7z x $name_decompressed > /dev/null 2>&1 && name_dec>
		else
				cat $name_decompressed; 
				exit 1
		fi
done
```




