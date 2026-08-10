
PC: Program Counter: 
- Guarda la direccion de la instruccion a ejecutar
- Un sumador incrementa el PC en +4 (tamaño de una instruccion: 4 Bytes)
IR: Registro de instrucciones

- ##### Memoria de instrucciones
	- Se guardan las instrucciones que componen el programa
	1. Entrada: Read Address-Dirección: dirección en la cual esta la instrucción. Tiene como entrada el PC
	2. Salida: Instrucción en si misma. 32 cables
	- Cada instruccion ocupa 4 Bytes-32 bits
	- La dirección de memoria de la instrucción se guarda en PC
- #### Banco de Registros
	- Entra la dirección del registro y sale el dato almacenado en el
	- 32 registros de 32 bits
	- Entradas (direcciones: 5 cables):
		1. Registro de lectura 1: entra la dirección del registro que quiero leer
		2. Registro de lectura 2: igual anterior
		3. Registro de escritura: entra la dirección del registro en el que quiero escribir
		4. Dato a escribir: dato que se va a escribir en el registro indicado en "Registro escritura". 32 cables
	- Salidas (datos: 32 cables):
		1. Dato leído 1: del registro indicado en "Registro lectura 1"
		2. Dato leído 2: del registro indicado en "Registro lectura 2"
	- ##### Señales de control:
		- RegWrite/EscrReg: 1-Habilita la escritura en un registro.
		- RegDest: Elige de donde viene la direccion en la que se escribe, segun el tipo de instruccion.
- #### ALU
	- Operaciones aritmetico logicas
	- Recibe 2 operandos y devuelve un resultado
	- 32 cables cada dato
	- ##### Señales de control:
		- ***ALUOp*** (3 bits): Define que operacion hay que hacer
		- ***ALUSrc/FuenteALU*** (1 bit): Elige si se lee un registro o un valor inmediato
- #### Memoria de Datos:
	- Guarda los datos, variables del programa
	- Se pueden leer o escribir datos
	- Tiene un retardo (latencia de lectura y de escritura)
	- Lectura: Se activa ***MemRead*** y el dato de la dirección ***Address*** sale por ***Read data***
	- Escritura: Se activa ***MemWrite*** y el dato de ***Write data*** se escribe en la dirección ***Address***
	- Entradas:
		1. ***Address*** (32 bits): dirección de memoria
		2. ***Write data*** (32 bits): dato a escribir
	- Salidas:
		1. ***Read data*** (32 bits): dato leído
	- ##### Señales de control:
		- ***MemRead*** (1 bit): 1-Habilita la lectura de memoria
		- ***MemWrite*** (1 bit): 1-Habilita la escritura en memoria
- #### Unidad de Control:
	- Genera las señales según el CodOp de la instrucción
	1. ***RegDest***: Selecciona el registro destino (Rt o Rd)
		- 0: viene de RT. 1: viene de RD.
	2. ***RegWrite***: Habilita la escritura en el banco de registros
	3. ***ALUSrc***: Decide si el segundo operando de la ALU es registro o valor inmediato. Va al Mux de la entrada 2 de la ALU.
		- 0: Lee de Registro. 1: Lee de Ext. de signo.
	4. ***ALUOp***: Indica a la ALU que operacion realizar
	5. ***MemRead/LeerMem***: Habilita lectura en memoria (***lw***)
	6. ***MemWrite/EscrMem***: Habilita escritura en memoria (***sw***)
	7. ***MemToReg/MemaReg***: Decide si el dato que se escribe en el registro viene de la ALU o de la Memoria
		- 0: sale de la ALU. 1: sale de la memoria.
	8. Branch/SaltoCond: Activa el salto condicional (***beq***, ***bneq***)
## Instrucciones
- 32 bits
- (31-26) CodOp 6 bits:
	- Determina que tipo de instruccion es
	- Va a la Unidad de Control:
		- Habilita las señales segun el tipo de instruccion
- (25-21) RS 5 bits
- (20-16) RT 5 bits
- (15-11) RD 5 bits
### Tipo R
- add, and
- Involucran 3 registros:
	- 2 de lectura
	- 1 de escritura
- Estructura:
	- (31-26) CodOp=0
	- (25-21) RS: Reg Lectura 1: De que registro se lee el primer dato
	- (20-16) RT: Reg Lectura 2: De que registro se lee el primer dato
	- (15-11) RD: Reg Escritura: En que registro se guarda el resultado
	- (10-6) -----
	- (5-0) Func: que operacion se hace
- El resultado de la operacion de la **ALU** va a "***Dato a escribir***". Se guarda en el *Registro de escritura*
- No usa la Memoria de Datos

### Tipo I
#### lw
- Lee un dato de memoria y lo guarda en un registro
- Estructura:
	- (31-26) CodOp: unico para cada instruccion
	- (25-21) RS: Direccion de memoria: a esta direccion le suma el offset y lee el dato de esa direccion
	- (20-16) RT: Reg destino: Guarda el dato en este registro
	- (15-0) OFFSET: Se suma este valor a la direccion RS
#### sw
- Lee un dato de un registro y guarda en memoria
- Estructura:
	- (31-26) CodOp: unico para cada instruccion
	- (25-21) RS: Direccion de memoria: a esta direccion le suma el offset y guarda el dato en esa direccion
	- (20-16) RT: Reg origen: Lee el dato de este registro
	- (15-0) OFFSET: Se suma este valor a la direccion RS