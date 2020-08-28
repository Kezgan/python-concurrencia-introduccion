# To `join()` or not to `join()`...

En `dormilones.py` vimos tres ejemplos básicos de ejecución:

- Clásico secuencial,
- Con threads,
- Y con threads, pero esperando a que terminen usando `join()`.

Entonces responda:
- ¿Por qué los segundos que se imprimen que pasaron son 2, 0 y 1 (aprox.) respectivamente?
    + En el secuencial son 2 segundos aproximadamente porque el código se ejecuta línea por línea. Primero inicia el contador, luego se ejecutan los dos dormir() que hacen que el contador espere 2 segundos, y al final el contador finaliza. En el ejemplo con threads se ejecuta el código de forma concurrente (múltiples hilos). Por último, el ejemplo con threads "secuencial" se ejecuta de forma concurrente pero utilizando join(), haciendo que primero finalice el conteo de t1 y t2.
- ¿Cuántos hilos o threads hay en cada caso?
- Los últimos dos ejemplos tienen la misma cantidad de threads cada uno, ¿cuál sería la diferencia entonces?
- En el último ejemplo, ¿qué desventaja o desventajas le ve al uso del `join()`?


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


# Intercalación en concurrencia

**Dos reglas importantes** para `contadorConcurrente.py`:
- Mirá el código pero _no lo ejecutes_,
- Mirá el código pero _no lo ejecutes_.

(Referencia [The First Rule of Fight Club (1999)](https://www.youtube.com/watch?v=dC1yHLp9bWA))

Mirando el código de `contadorConcurrente.py`, pero sin ejecutarlo:
- Al ejecutar la función `cuenta()`, ¿cuántas veces se ejecuta el `for` que tiene adentro, y qué hace cada iteración del `for`?
- ¿Es verdad que cada thread lanza una ejecución de la función `cuenta()`?
- ¿Es verdad que se está esperando a que termine cada thread?
- ¿Cúal te parece que es el valor que se imprime de `counter`?

Ahora corré `contadorConcurrente.py`:
- Correlo varias veces, ¿qué observás que pasa?
- ¿Por qué está pasando eso que observás?


# ¿Secuencial clásico, concurrente o paralelo?

Para cada una de las siguiente situaciones, decidí si es secuencial clásico, concurrente o paralelo. Intentá justificar señalando las ideas esenciales de cada caso.

- Cuál persona de un total de 50 corre más rápido una maratón.
    - opción 1) Cada persona corre secuencialmente en la pista, y medimos cada tiempo.
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
