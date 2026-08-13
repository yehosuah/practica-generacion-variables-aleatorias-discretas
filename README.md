# Práctica 2 - Generación de variables aleatorias discretas

Solución reproducible en un notebook Jupyter autocontenido, con resultados auditables y una versión HTML ya ejecutada.

## Contenido

- `practica_2_solucion.ipynb`: notebook autocontenido que presenta y ejecuta toda la solución.
- `practica_2_solucion.html`: versión estática del notebook con sus salidas.
- `resultados/`: tablas CSV, resumen JSON y figuras producidas por el programa.

## Ejecución

Abra `practica_2_solucion.ipynb` en Jupyter y ejecute todas las celdas. Requiere Python 3 con NumPy, pandas y Matplotlib. Desde terminal:

```bash
jupyter nbconvert --to notebook --execute practica_2_solucion.ipynb \
  --output practica_2_solucion.ipynb --ExecutePreprocessor.timeout=300
jupyter nbconvert --to html practica_2_solucion.ipynb \
  --output practica_2_solucion.html
```

## Hallazgos principales

- **Inventario:** con 3 botellas, las métricas teóricas son 2.25 ventas/día, 0.25 ventas perdidas/día, 0.75 botellas sobrantes/día y un nivel de servicio por unidades de 90%. Sin costos unitarios no existe una decisión económica única. Tres botellas es óptimo cuando el costo de una venta perdida es mayor que el costo de sobrante, pero no más de cuatro veces ese costo.
- **Puntos fijos de una permutación de 100 cartas:** esperanza exacta 1 y varianza exacta 1; la simulación se contrasta con ambos valores.
- **Colección de sumas de dos dados:** se reporta simulación, intervalo de confianza y el valor exacto calculado por programación dinámica sobre los 2,048 estados posibles.
- **Integrales:** las siete aproximaciones Monte Carlo incluyen error estándar, intervalo de confianza y comparación con su valor analítico.

## Nota sobre el ejercicio 4

El enunciado pide usar “la secuencia de números aleatorios del texto”, pero dicha secuencia no aparece en el PDF proporcionado. Por eso el notebook implementa el procedimiento eficiente correcto -generar posiciones de los fallos mediante saltos geométricos- y muestra una corrida reproducible con una semilla documentada. La función también acepta cualquier secuencia externa para obtener exactamente la respuesta correspondiente al texto.

Con 25 variables y probabilidad de fallo 0.2, el número esperado de uniformes del algoritmo implementado es `25(0.2) + 0.8 = 5.8`: se usa un uniforme por cada fallo y uno terminal cuando la última variable es éxito.

## Reproducibilidad

Todas las semillas, tamaños muestrales y transformaciones están declarados dentro del notebook. Los archivos de `resultados/` se regeneran desde cero en cada ejecución.

> **Nota sobre el historial Git:** los timestamps del 13 de agosto de 2026 fueron configurados deliberadamente para demostrar el control de metadatos de autor y committer en Git. No representan la fecha real de creación o publicación del proyecto.
