- Lenguaje:
	- interpretado
	- case sensitive
	- layout (espacios)
	- tipado debil

$file archivo se fija que tipo de archivo es

ejemplo script
#!/bin/bash

#comentario
echo "Hola Mundo"

exit 0

	$ chmod +x hola.sh
le da permiso de ejecucion
- ls -l
	- -  r | w | x  -  r | - | x  -  r | - | -
	-     dueño      grupo      cualq otro
hvu

	$ ./hola.sh
	$ echo $?
0


/usr %% ruta absoluta %%
share/foto.gif %% ruta relativa %%