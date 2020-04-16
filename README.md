# Manejo de colecciones en Java  

## Introducción
* Colección. Contenedor para un conjunto de elementos de un tipo en una sola unidad
* Paquete *java.util*
* Framework de Colecciones en Java
> * Interfaces
> * Implementaciones
> * Algoritmos

## Tipos de colecciones y ejemplos de uso  
### Iterable<E>
* Nos permite recorrer sucesión de elementos
* A partir de Java 8, se permite eliminar
----

### Collection<E>
* Extiende de Iterable<E>
* size, isEmpty, add, remove, iterator, containsAll..., toArray, stream
----

### Set<E>
* Collection<E> que **no permite duplicados**
* Sin acceso posicional
* Uso de genéricos
* Operador diamond <> para una sentencia menos "verbose"

#### HashSet<E>
* Almacenar valores en tabla hash, la mayoría de las operaciones son en un tiempo constante
* Permite valores nulos
* No se puede predecir el orden

#### LinkedHashSet<E>
* Almacena los valores en una tabla doblemente enlazada.
* Mantiene el orden de inserción

#### TreeSet<E>
* Almacena sus valores en un *red-black*
* Nos permite mantener los elementos en orden, con una eficiencia bastante razonable
* Los elementos deben implementar *Comparable*
----

### List<E>
* Permite duplicados
* Acceso posicional
* Búsqueda
* Iteración extendida. Permitiendo avanzar en cualquier dirección, añadir, modificar y eliminar
* Se puede obtener un *view* 

#### ArrayList<E>
* Acceso por índice
* Inserción, en media
* Menos espacio que LinkedList

#### Queue<E>
* Lanzan una excepción: add(e), remove(), element()
* Devuelven valor especial: offer(e), poll(), peek()

#### [Deque<E>](./deque.md)
* Puede trabajar como cola, pila o cola doble
----

### Map<K,V>
* No hereda de Collection<E>
* Maneja pares *clave, valor*
* No puede haber claves repetidas y pueden existir nulas
* No permite almacenar tipos primitivos; hay que usar los tipos wrapper en su lugar (int -> Integer)

#### MapEntry<K,V>
* Permite consultar un par *clave, valor*
* Se puede obtener un Set <Map.Entry<K,V>> a través del método Map.entrySet()

#### Operaciones con Map<K,V>
* Insertar clave y valor *put(key, value)*
* Obtener valor en base a la clave *get(key)*
* Consultar si están contenidos clave o valor *containsKey(key) / containsValue(value)*
* Eliminar el par clave, valor `remove(key)`

#### Implementaciones de Map<K,V>
##### HashMap<K,V>
* **No existe orden sobre los pares**
* El tiempo de ejecución de inserción y consulta es constante
* No es sincronizada

> * Insertar con *put()* una referencia que ya existe, simplemente reemplaza el valor
> * Con *putIfAbsent()* se puede insertar un valor sí y solo sí la clave no existe, devolviendo dicho valor en este caso, y sino *null*.
> * Se puede comprobar si existe una clave o valor mediante *containsKey() / containsValue()*
> * Devolver un valor predefinido con *getOrDefault()* en caso de no existir dicho valor

##### LinkedHashMap<K,V>
* **Ordena los pares clave,valor según su inserción**
* Rinde algo peor que HashMap.
* No es sincronizada


##### TreeMap<K,V>
* **Mantiene las claves en orden(natural)**
* Peor rendimiento de Map.
* No puede tener ninguna clave nula, aunque sí los valores

----
### Colecciones no modificables
* Si se tratan de modificar lanzan una excepción
* Un ejemplo es usarlas como resultado de una operación

### Colecciones sincronizadas
* Aptas para un contexto multihilo

### Otras implementaciones menos usadas
* EnumSet, CopyOnWriteArraySet, CopyOnWriteArrayList, EnumMAp, WeakHashMap, IdentityHashMap, LinkedBlockingDeque, PriorityQueue

----
## Algunos algoritmos para colecciones  

### Algoritmos de ordenación
* Collections.sort(list)
* Collections.sort(list, comparator)

### Algoritmos de desordenación
* Collections.shuffle(list)
* Collections.shuffle(list, random)

### Algoritmos de búsqueda
Devuelve el índice del elemento si lo encuentra (no garantiza cúal de ellas) y `-1` si no lo encuentra

### Algoritmos para algunas operaciones
* Collection.max(list)
* Collection.min(list)
* Collection.frequency(list)
* Collection.disjoint(list, list) - Devuelve true o false según tengan elementos en común

## Librerías de colecciones de terceros  
* Guava
* Eclipse Collections
* Apache Commons Collections
----

Resumen de <https://openwebinars.net/academia/aprende/colecciones-java/>
