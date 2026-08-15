no se puede aplicar map a cualquier tad
fmap :: (a->b) -> f a -> f b
aplica una funcion a todos los elementos de a almacenados en f a

los constructores de tipos que poseen una funcion fmap son functores

functor.1
fmap id = id
functor.2
fmap f . fmap g = fmap (f.g)

class Functor f where
	fmap :: (a->b) -> f a -> f b
	