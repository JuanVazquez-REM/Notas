# Requisitos 
Estos requisitos estan dirijidos para acceder a una conexion [[SSH]] por medio de fuerza bruta.

1. Estar en la maquina vicctima con usuario root.
2. Buscar los usuarios creados en la maquina con  *cat /etc/passwd*.

*Nota*
Los usuarios mayores a 1000:1000 son usuarios, y con terminacion /bin/bash.

3. Utilizar [[Hydra]] para los ataques de fuerza bruta.