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
