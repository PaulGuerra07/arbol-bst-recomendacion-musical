# Árbol de Recomendación Musical

Unidad 3 de Estructuras de Datos: árboles. Este repositorio reúne los dos trabajos de la unidad — la implementación de un árbol binario de búsqueda y el análisis comparativo de estructuras de árbol aplicado a un caso de negocio real.

## Tema 2 — Implementación: BST para una playlist

Una playlist se modela como un árbol binario de búsqueda donde la clave de cada nodo es la duración de la canción en segundos. El árbol se construye con nodos y punteros propios, sin usar listas nativas de Python.

| Operación | Detalle |
| --- | --- |
| Insertar | Inserción iterativa respetando la propiedad del BST |
| Eliminar | Los tres casos: hoja, un hijo y dos hijos con sucesor en orden |
| Tiempo total | Suma recursiva de las duraciones de todo el árbol o de un subárbol |
| Recomendar canción | Descenso por el árbol guardando la menor diferencia absoluta hasta hallar la duración más cercana a la pedida |
| Filtrar cortas | Poda recursiva de los nodos por debajo de un umbral, reenlazando los punteros |
| Promedio | Duración media a partir del total y el conteo recursivo |
| Recorrido en orden | Devuelve las duraciones ordenadas de menor a mayor |

El árbol se dibuja con Matplotlib calculando las coordenadas de cada nodo de forma recursiva, con el espaciado horizontal reducido en cada nivel.

**Requisitos**

```
pip install ipywidgets matplotlib
```

**Ejecución**

Abrir `Guerra_Paul_Estructura_U3T2.ipynb` y ejecutar la celda. La interfaz carga una playlist de ejemplo y permite insertar, eliminar, filtrar y pedir recomendaciones sobre ella.

## Tema 1 — Análisis: BST, AVL y Rojo-Negro en un motor antifraude

Comparación de las tres estructuras sobre el mismo conjunto de ocho transacciones bancarias, midiendo altura resultante y pasos de búsqueda.

| Estructura | Altura | Pasos para hallar el ID 670 |
| --- | --- | --- |
| BST | 8 niveles (degenerado) | 7 |
| AVL | 4 niveles | 2 |
| Rojo-Negro | 4 niveles | 2 |

Informe completo: [docs/informe-arboles-bst-avl-rojo-negro.md](docs/informe-arboles-bst-avl-rojo-negro.md)

---

**Paúl Andrés Guerra Vicuña** · Estructuras de Datos · Ingeniería en Ciencias de Datos e Inteligencia Artificial · Universidad Nacional de Chimborazo (UNACH)
# Árbol de Recomendación Musical

Unidad 3, Tema 2 de Estructuras de Datos: árboles binarios de búsqueda. Una playlist se modela como un BST donde la clave de cada nodo es la duración de la canción en segundos.

## Operaciones implementadas

| Operación | Detalle |
| --- | --- |
| Insertar | Inserción iterativa respetando la propiedad del BST |
| Eliminar | Los tres casos: hoja, un hijo y dos hijos con sucesor en orden |
| Tiempo total | Suma recursiva de todos los nodos |
| Recomendar canción | Descenso por el árbol buscando la duración más cercana a la pedida |
| Filtrar cortas | Poda recursiva de los nodos por debajo de un umbral |
| Promedio | Duración media a partir del total y el conteo recursivo |
| Recorrido en orden | Devuelve las duraciones ordenadas de menor a mayor |

## Visualización

El árbol se dibuja con Matplotlib calculando las coordenadas de cada nodo de forma recursiva, con el espaciado horizontal reducido en cada nivel.

## Requisitos

```
pip install ipywidgets matplotlib
```

## Ejecución

Abrir `Guerra_Paul_Estructura_U3T2.ipynb` y ejecutar la celda. La interfaz carga una playlist de ejemplo y permite insertar, eliminar, filtrar y pedir recomendaciones sobre ella.

---

**Paúl Andrés Guerra Vicuña** · Estructuras de Datos · Ingeniería en Ciencias de Datos e Inteligencia Artificial · Universidad Nacional de Chimborazo (UNACH)
