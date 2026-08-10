# Modelos de casos de uso


## Casos de uso y valor añadido
### Actor:
Es algo con comportamiento, como una persona (identificada por un rol), un sistema informatizado o una organizacion.
### Escenario (instancia de caso de uso):
Es una secuencia especifica de acciones e interacciones entre los actores y el sistema objeto de estudio.
Es una historia particular del uso de un sistema, o un camino a traves del caso de uso
### Caso de uso:
Es una coleccion de escenarios con exito y fallo relacionados, que describe a los actores utilizando un sistema para satisfacer un objetivo

## TIpos de casos de uso y formatos
### Caso de uso de caja negra
Es la clase mas comun y recomendada, no describe el funcionamiento interno del sistema, sino que se describe el sistema en base a las responsabilidades que tiene.
Define ***que*** debe hacer el sistema (requisitos funcionales), sin decir el ***como*** (diseño)
### Tipos (grados) de formalidad
- Breve: resumen conciso de un parrafo, normalmente del escenario de exito principal.
- Informal: multiples parrafos que comprenden varios escenarios.
- Completo: se escriben con detalle todos los pasos y variaciones, y hay secciones de apoyo como precondiciones y garantias de exito.


## 6.9 Actores principales, objetivos y casos de uso

Procedimiento basico:
1. Elegir limites del sistema: 
2. Identificar actores principales: aquellos que tienen objetivos de usuario que se satisfacen mediante el uso de los servicios del sistema
3. Para cada uno, identificar sus objetivos de usuario
4. Definir los casos de uso que satisfagan los objetivos de usuario, nombrarlos de acuerdo con sus objetivos


## 6.12 Actores

- **Actor principal:** tiene objetivos de usuario que se satisfacen mediante el uso de los servicios del sistema.
	- *Por que se identifica?:* para encontrar los objetivos de usuario.
- **Actor de apoyo:** proporciona un servicio al sistema. Normalmente otro sistema, tambien puede ser otra organizacion o persona.
	- *Por que se identifica?:* Para clarificar las interfaces externas y protocolos.
- **Actor pasivo:** esta interesado en el comportamiento del caso de uso, pero no es principal o de apoyo.
	- *Por que se identifica?:* Para asegurar que todos los intereses necesarios se han identificado y satisfecho.
## 6.16 Casos de 