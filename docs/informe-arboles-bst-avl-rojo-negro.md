# Árboles de búsqueda en un motor antifraude bancario

**Estructuras de Datos — Unidad 3, Tema 1: Árboles**

Análisis comparativo de tres estructuras de árbol (BST, AVL y Rojo-Negro) aplicadas al módulo de procesamiento de transacciones en tiempo real de un banco digital.

## El problema de negocio

El área de Operaciones y Seguridad Transaccional procesa transferencias, pagos con tarjeta y retiros en milisegundos. Cada transacción tiene un ID numérico único y un nivel de riesgo asignado por el motor antifraude, donde 1 es una operación normal y 5 un fraude crítico.

Si localizar o actualizar una transacción tarda demasiado, el banco aprueba pagos fraudulentos o bloquea pagos legítimos. Una vez que el dinero sale del sistema financiero nacional, la operación ya no se puede revertir. La latencia, aquí, no es un problema de rendimiento: es una falla de seguridad financiera.

## Conjunto de prueba

Las mismas ocho transacciones se insertaron en las tres estructuras, en orden ascendente de ID, para poder compararlas de forma justa:

`130,1 — 210,2 — 350,3 — 480,5 — 540,3 — 670,4 — 890,5 — 920,2`

En cada árbol se ejecutaron las mismas tres operaciones: inserción de las ocho transacciones, búsqueda del ID 670 (riesgo alto, que el motor necesita confirmar de inmediato) y eliminación del ID 130 (transacción ya conciliada y archivada).

## Resultados

| Estructura | Altura final | Pasos para hallar el ID 670 | Mecanismo de balanceo |
| --- | --- | --- | --- |
| Árbol Binario de Búsqueda | 8 niveles (degenerado) | 7 | Ninguno |
| Árbol AVL | 4 niveles | 2 | Rotaciones simples, cuatro durante la inserción |
| Árbol Rojo-Negro | 4 niveles | 2 | Recoloreo, con rotaciones solo cuando es estrictamente necesario |

## Análisis

### Árbol Binario de Búsqueda

El BST organiza correctamente las transacciones (menores a la izquierda, mayores a la derecha), pero esa lógica por sí sola no garantiza eficiencia. Como los ocho IDs llegaron en orden ascendente, cada nodo nuevo quedó colgando del anterior por la derecha y el árbol degeneró en una lista enlazada: ninguna rama hacia la izquierda, ocho niveles de altura.

Esto importa porque los IDs de transacción suelen generarse con contadores autoincrementales, que es exactamente el caso que degrada el BST. Buscar la transacción 890 obligó a comparar la cadena completa: 130 → 210 → 350 → 480 → 540 → 670 → 890. El tiempo de búsqueda pasa a ser proporcional al total de operaciones del día, y el motor antifraude pierde la ventana de milisegundos que tiene para congelar un pago.

Conclusión: el BST sirve para entender la lógica de comparación y ordenamiento, y es utilizable con conjuntos pequeños o estáticos. No es confiable para un banco con alto volumen transaccional.

### Árbol AVL

El AVL detectó el desbalance ya en la tercera inserción y ejecutó una rotación simple a la izquierda, dejando el 210 como nueva raíz del subárbol. Ese patrón se repitió tres veces más (en los nodos 350, 210 y 540) hasta llegar a una estructura final de cuatro niveles, la mitad de la altura que alcanzó el BST.

La búsqueda del ID 670 tomó 2 pasos (raíz 480 → derecha 670) frente a los 6 que habría tomado en el BST degenerado. La eliminación del 130 se resolvió reorganizando automáticamente el subárbol izquierdo, sin intervención manual.

El AVL garantiza O(log n) en inserción, búsqueda y eliminación sin importar el orden de llegada de los IDs, y elimina por completo el riesgo de que la estructura se deforme en una lista.

### Árbol Rojo-Negro

El Rojo-Negro alcanzó el mismo rendimiento de búsqueda que el AVL (2 pasos para el ID 670) pero con una filosofía distinta: en lugar de exigir balance perfecto en todo momento, permite un desbalance moderado y lo controla mediante las propiedades de color, recurriendo a rotaciones solo cuando es estrictamente necesario.

Al eliminar el ID 130, el algoritmo corrigió el balance recoloreando los nodos afectados (210 pasó de rojo a negro y 350 de negro a rojo) en lugar de ejecutar una rotación completa. En un sistema real eso se traduce en menos operaciones de reestructuración interna.

## Recomendación

Para el núcleo del motor de transacciones de un banco digital, donde las inserciones y eliminaciones son masivas y constantes, el **Árbol Rojo-Negro** es la estructura más conveniente: ofrece balance suficiente con menor costo de mantenimiento por operación.

El **AVL** es preferible cuando las búsquedas son mucho más frecuentes que las modificaciones, porque mantiene el árbol más estrictamente balanceado.

El **BST simple** queda descartado para este escenario.

---

**Paúl Andrés Guerra Vicuña** · Estructuras de Datos · Ingeniería en Ciencias de Datos e Inteligencia Artificial · Universidad Nacional de Chimborazo (UNACH)
