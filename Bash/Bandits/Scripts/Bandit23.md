# Bandit23
Analisando el script [[Archivos#Cron]] que de
```bash
#!/bin/bash

myname=$(whoami)

cd /var/spool/$myname/foo
echo "Executing and deleting all scripts in /var/spool/$myname/foo:"
for i in * .*;
do
    if [ "$i" != "." -a "$i" != ".." ];
    then
        echo "Handling $i"
        owner="$(stat --format "%U" ./$i)"
        if [ "${owner}" = "bandit23" ]; then
            timeout -s 9 60 ./$i
        fi
        rm -f ./$i
    fi
done
```

	for i in * .*;
Recorre todos los archivos de un directorio

	if [ "$i" != "." -a "$i" != ".." ];
Condicion para ignorar archivos . y ..
El . hace referencia al directorio actual
-a es igual que un AND
El .. hace referencia al retroceso del directorio

	if [ "${owner}" = "bandit23" ]; then
		timeout -s 9 60 ./$i
	fi
Si el propietario es bandit23 vas ejecutar el archivo cada cierto tiempo
