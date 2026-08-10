## TCP


#### Ejemplo http
se abre el pedido, se envia la informacion y despues se cierra

el cliente web inicia la conexion el servidor la acepta y a partir de ahi 

## Maquina de estados

### 3 way handshake
#### Servidor
Crea el socket y a partir de la directiva listen cambia el estado de closed a listen, queda a la espera escuchando
Cuando le llega el SYN manda SYN + ACK
Queda a la espera de recibir el ACK del cliente, ahi pasa a estado established

#### Cliente
Crea el socket y ejecuta el connect que envia SYN al servidor
Al recibir el ACK del servidor ya queda en estado ESTABLISHED


### Cierre de la conexion
#### Desde el lado que se cierra:
- Desde la aplicacion se envia la directiva close que envia el FIN
	- Si llega ACK se queda a la espera de que le llegue el fin
	- Si llega FIN + ACK, envia ACK y 

#### Desde el lado que recibe el FIN
- Se recibe el FIN y se manda el ACK
- Queda a la espera de la directiva **CLOSE**
- Cuando llega la directiva **CLOSE** envia el ultimo ACK y cierra la conexion

## Temporizadores TCP
- ### Retransmision
	Al vencer retransmite el ultimo segmento, se ajusta de forma continua segun el RoundTripTime
- ### Persistencia
	- Cuando el tamaño de ventana se agota, B envia un W=0
	- Si despues de un tiempo "Pers" no llega una actualizacion, A manda el ultimo Byte para recibir un ACK con el tamaño de ventana
- ### Keepalive
	- Cuando no hay datos para mandar permite mandar una señal de vida para asegurarse que la conexion este activa y deberia llegar una respuesta con **ACK**
- ### Time Wait
	- Cuando llega un close y llegaron todos los **ACK** espero un tiempo hasta que cierra definitivamente


## NAT
Dentro de una red privada