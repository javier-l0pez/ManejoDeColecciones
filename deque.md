# Deque
Se añadió en JDK 6.0. Como las implementaciones de cola, estas se diferencian en las características *bounded/unbounded, blocking/non-blocking,* y *thread-safe/non-thread-safe*.

La interfaz **Deque** ([Javadoc](https://docs.oracle.com/javase/7/docs/api/java/util/Deque.html)) hereda de java.util.Queue y la extiende con métodos para agregar elementos en la parte del principio del *Deque*, elminar la parte del final, y ver el elemento del final del *Deque* sin eliminarlo.

Dado que hereda de Queue, se han renombrado los métodos de la siguiente forma:

## Métodos

![Methods of Deque](https://www.geeksforgeeks.org/wp-content/uploads/Selection_034.png)

* `add(e)` añade el elemento al final.
* `offer(e)` añade un elemento al final y devuelve *boolean* para explicar si la inserción fue correcta.
* `iterator()` devuelve un iterador para este *deque*.
* `push(e)` añade el elemento al principio.
* `pop(e)` elimina un elemento del principio y lo devuelve.
* `poll(e)` Recoge y elimina el primer elemento del *deque*, o devuelve *null* si está vacía.
* `peek(e)` Recoge, pero no elimina, el primer elemento, o devuelve *null* si está vacía.
A estos se les puede añadir *First* o *Last* para especificar si se quiere del principio o final del *Deque* haciéndola funcionar como cola o pila.

## Ejemplo

```java
public class DequeExample {
  public static void main(String[] args) {
    Deque<Integer> dequeue = new ArrayDeque<>();
    dequeue.offerFirst(20); // -> 20
    dequeue.offerFirst(21); // -> 21 20
    dequeue.offerFirst(22); // -> 22 21 20
    dequeue.offerLast(23);  // -> 22 21 20 23
    dequeue.offerLast(24);  // -> 22 21 20 23 24
    dequeue.offerLast(25);  // -> 22 21 20 23 24 25
    dequeue.offerFirst(26); // -> 26 22 21 20 23 24 25
    dequeue.offerFirst(27); // -> 27 26 22 21 20 23 24 25
    System.out.println("dequeue = " + dequeue);

    System.out.println();
    System.out.println("dequeue.offerLast(28) = " + dequeue.offerLast(28));
    System.out.println("dequeue.offerFirst(29) = " + dequeue.offerFirst(29));
    System.out.println("dequeue = " + dequeue);

    while (!dequeue.isEmpty()) {
      System.out.println();
      System.out.println("dequeue.pollFirst() = " + dequeue.pollFirst());
      System.out.println("dequeue.pollLast() = " + dequeue.pollLast());
      System.out.println("dequeue = " + dequeue);
    }
  }
}
```

Con varias llamadas a `offerFirst()` y `offerLast()`, el programa rellena el *Deque*, lo imprime en pantalla, y luego elimina elementos alternativamente de ambos lados hasta que el Deque quede vacío.

Esta es la salida del programa:

```java
dequeue = [27, 26, 22, 21, 20, 23, 24, 25]

dequeue.offerLast(28) = true
dequeue.offerFirst(29) = true
dequeue = [29, 27, 26, 22, 21, 20, 23, 24, 25, 28]

dequeue.pollFirst() = 29
dequeue.pollLast() = 28
dequeue = [27, 26, 22, 21, 20, 23, 24, 25]

dequeue.pollFirst() = 27
dequeue.pollLast() = 25
dequeue = [26, 22, 21, 20, 23, 24]

dequeue.pollFirst() = 26
dequeue.pollLast() = 24
dequeue = [22, 21, 20, 23]

dequeue.pollFirst() = 22
dequeue.pollLast() = 23
dequeue = [21, 20]

dequeue.pollFirst() = 21
dequeue.pollLast() = 20
dequeue = []
```

## Interfaz BlockingDeque
Parecido a *BlockingQueue*, java.util.concurrent.BlockingDeque ([Javadoc](https://docs.oracle.com/en/java/javase/14/docs/api/java.base/java/util/concurrent/BlockingDeque.html)) ofrece más operaciones de bloqueo que esperan hasta que un elemento está disponible cuando se borra un elemento del *Deque*, o esperan hasta que un espacio está disponible cuando se insertan elementos.
