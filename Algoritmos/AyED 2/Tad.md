## P3
- Un tipo no es solamente un conjunto de valores
- Un tipo de datos queda definido dando:
	- El conjunto de valores que puede tomar
	- Un conjunto de operaciones definidas sobre estos valores
	- Un conjunto de propiedades que relacionan todo lo anterior
- Ej: Que es una cola?
	- Es una estructura a la cual se puede:
		- Agregar elementos
		- Obtener el primer elemento
		- Quitar el primer elemento
		- Preguntar si esta vacia
	- Existe una relacion entre el orden en que se agregan y quitan elementos (FIFO)
- Esta descripcion es abstracta porque refleja el comportamiento pero no la implementacion
## P4
- La idea de un TAD es abstraer detalles de la implementacion
- La especificacion del TAD es la descripcion formal del comportamiento esperado
- Un usuario es alguien que usa las operaciones del TAD
- El implementador es el que provee el codigo que satisface la especificacion
- El usuario solo puede suponer lo especificado
- La forma usual de especificar un TAD es mediante una especificacion algebraica.
## P5-6
Para proveer un TAD debemos dar:
- Un nombre al tipo y definir el conjunto de datos.
	- Ej Lista:
		- Nombre tipo: Lista
		- Almacena: cualquier otro tipo (siempre que sean todos del mismo tipo)
- Sus operaciones
	- Ej Cola:
		- Agregar elemento
		- Quitar elemento
		- Acceder al primer elemento
		- Saber si la cola esta vacia
- Una especificacion del comportamiento
	- Describir operaciones y ecuaciones entre operaciones (y describirlas)
Ej tad Cola:
tad Cola (A : Set) where
	vacia : Cola A (constructor)
	poner: A -> Cola A -> Cola A (constructor)
	primero: Cola A -> A (inspector)
	sacar: Cola A -> Cola A (no es constructor)
	esVacia: Cola A -> Bool
	largo: Cola A -> Int
	%% El lenguaje con el cual se definen los TAD esta en "The Larch Book" - Guttag Horning %%

---
esVacia vacia = true
esVacia (poner x q) = false
primero (poner x vacia) = x
primero (poner x (poner y q)) = primero (poner y q)
sacar (poner x vacia) = vacia
sacar (poner x (poner y q)) = poner x (sacar (poner y q))

---
es casi como una implementacion, pero:
- no hay pattern matching
- no hay orden de evaluacion
- cada linea es un predicado verdadero
## P7
Un TAD puede admitir varias implementaciones:
Ej Cola:
- vacia = []
- poner = (:)
- primero = last
- sacar = init
- esVacia = null
otra opcion
- vacia = []
- poner x xs = (xs ++ [x])
- primero = head
- sacar = tail
- esVacia = null
## P8 - Implementaciones

## P9 - Implementaciones en Haskell
class Cola t where
	vacia :: t a
	poner :: a -> t a -> t a
	sacar :: t a -> t a
	primero :: t a -> a
	esVacia :: t a -> Bool
	// t a significa que es una Cola (t) de elementos de tipo a
instance Cola [] where
	vacia = []
	poner = (:)
	primero = last
	sacar = init
	esVacia = null


## P14 - Principio de extensionalidad
Dadas 2 funciones f, g :: X -> Y
f = g <=> V x :: X . f x = g x
## P15 - Analisis por casos
Solo casos finitos (como Bool)
not :: Bool -> Bool
not False = True
not True = False
Caso x = False
	not (not False)
	= <not o 1>
	not True
	= <not o 2>
	False
## P16-17 - Induccion Estructural
Definicion:
Dada una propiedad P sobre un TAD T
para probar V t :: T . P(t):
- probamos P para todo t dado por un constructor no recursivo
- para todo t dado por un constructor recursivo probamos que si P (ti) para i = 1..k entonces P (t)