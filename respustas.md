# To `join()` or not to `join()`...

En `dormilones.py` vimos tres ejemplos básicos de ejecución:

- Clásico secuencial,
- Con threads,
- Y con threads, pero esperando a que terminen usando `join()`.

Entonces responda:
- ¿Por qué los segundos que se imprimen que pasaron son 2, 0 y 1 (aprox.) respectivamente?
    + En el secuencial son 2 segundos aproximadamente porque el código se ejecuta línea por línea. Primero inicia el contador, luego se ejecutan los dos dormir() que hacen que el contador espere 2 segundos, y al final el contador finaliza.
    En el ejemplo con threads se ejecuta el código de forma concurrente (múltiples hilos), finalizando la ejecución sin importar que todavía no haya terminado la ejecución de los hilos t1 y t2.
    Por último, el ejemplo 3 se ejecuta de forma concurrente "secuencial" utilizando join(), haciendo que el código espere a que finalice la tarea de los hilos t1 y t2, que terminarían aproximadamente al mismo tiempo.
- ¿Cuántos hilos o threads hay en cada caso?
    + En el primer caso hay un solo hilo (MainThread), y en los dos últimos hay tres hilos: MainThread y los dos hilos t1 y t2.
- Los últimos dos ejemplos tienen la misma cantidad de threads cada uno, ¿cuál sería la diferencia entonces?
    + La diferencia es que en el segundo ejemplo de threads se utiliza join(), que hace que el código espere a que finalice la tarea de los hilos t1 y t2.
- En el último ejemplo, ¿qué desventaja o desventajas le ve al uso del `join()`?
    + 


# Muchos threads

En `muchosThreads.py` hay algunas cosas básicas de Python:
- `from tiempo import Contador` importa desde `tiempo.py` la clase `Contador`.
- Cómo crear una lista vacía.
- Cómo hacer un loop con cantidad de iteraciones fija.
- Cómo agregar elementos (al final) a una lista.
- Cómo hacer un loop que itere sobre una lista.

## Parte 1
Mirá el código y fijate de entender la sintaxis. 

## Parte 2
Ahora corré el script: ¿por qué tarda lo que tarda? 
  + Lo que sucede en el código es que al entrar al primer for se crean los 10 hilos aproximadamente al mismo tiempo con un tiempo de sleep de 1.5 segundos. Al entrar al segundo for se hace join a los hilos creados previamente, y como finalizarán también aproximadamente al mismo tiempo el tiempo final que tardarán es de 1.5. Si en vez de 10 hilos creamos 20 tardarían lo mismo.

# Intercalación en concurrencia

**Dos reglas importantes** para `contadorConcurrente.py`:
- Mirá el código pero _no lo ejecutes_,
- Mirá el código pero _no lo ejecutes_.

(Referencia [The First Rule of Fight Club (1999)](https://www.youtube.com/watch?v=dC1yHLp9bWA))

Mirando el código de `contadorConcurrente.py`, pero sin ejecutarlo:
- Al ejecutar la función `cuenta()`, ¿cuántas veces se ejecuta el `for` que tiene adentro, y qué hace cada iteración del `for`?
  + El for se ejecuta la cantidad de veces que dice MAX_COUNT, pero distribuido en la cantidad de threads.
  + Cada iteración suma 1 en la variable counter.
- ¿Es verdad que cada thread lanza una ejecución de la función `cuenta()`?
  + Si, cuenta() se ejecutará el numero de threads que hayan.
- ¿Es verdad que se está esperando a que termine cada thread?
  + El join() espera a que termine el primer thread para luego ejecutar el segundo, pero el print muestra en pantalla hasta donde llegó la variable counter, sin esperar a que el segundo thread termine.
- ¿Cúal te parece que es el valor que se imprime de `counter`?
  + El valor counter siempre va a ser 1000000, pero lo que va a imprimir siempre va a ser un valor entre 500000 y 1000000, ya que print no espera a que ambos threads finalicen.

Ahora corré `contadorConcurrente.py`:
- Correlo varias veces, ¿qué observás que pasa?
  + Cada vez que se corre el valor varía.
- ¿Por qué está pasando eso que observás?
  + Al finalizar el primer thread puede pasar que se haya ejecutado una parte del segundo thread, mostrando el print un valor que varía entre 500000 y 1000000.


# ¿Secuencial clásico, concurrente o paralelo?

Para cada una de las siguiente situaciones, decidí si es secuencial clásico, concurrente o paralelo. Intentá justificar señalando las ideas esenciales de cada caso.

- Cuál persona de un total de 50 corre más rápido una maratón.
    - opción 1) Cada persona corre secuencialmente en la pista, y medimos cada tiempo.
      + 
    - opción 2) Todas las personas corren en la misma pista, y la que llega primero listo.
		- Preguntas: ¿hay algún recurso compartido? ¿genera problemas?
    - opción 3) Cada persona corre en una pista distinta, todas al mismo tiempo.
		- Pregunta: ¿hay un aumento de recursos respecto al anterior?
    - Pregunta: ¿pros y contras de cada opción?

- Competencia de triples en basquet: quién mete más en 10 intentos.
    - opción 1) Cada persona secuencialmente realiza 10 intentos, y anotamos la cantidad de triples.
    - opción 2) Todas las personas tiran los 10 intentos al mismo tiempo.
		- Preguntas: ¿hay algún recurso compartido? ¿genera problemas?
    - opción 3) Cada persona tira en un aro distinto, todas al mismo tiempo.
    - Pregunta: ¿pros y contras de cada opción?
