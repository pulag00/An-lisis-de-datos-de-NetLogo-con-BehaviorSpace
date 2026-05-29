# Análisis de datos de NetLogo con BehaviorSpace y Google Colab

## Modelo Virus - Análisis del parámetro `infectiousness`

Este repositorio contiene el desarrollo de un proyecto de análisis de datos generados desde un modelo de simulación en **NetLogo**, utilizando **BehaviorSpace** para ejecutar múltiples corridas experimentales y **Google Colab con R** para procesar, graficar e interpretar los resultados.

El modelo seleccionado fue **Virus.nlogox**, un modelo de propagación epidémica basado en agentes. El parámetro analizado fue `infectiousness`, el cual representa la capacidad de contagio de la enfermedad dentro de la población simulada.

---

## Objetivo del proyecto

Analizar cómo el parámetro `infectiousness` afecta:

1. La duración de la epidemia, medida mediante la variable `ticks`.
2. La evolución temporal de la cantidad de tortugas enfermas, medida mediante:

```netlogo
count turtles with [sick?]

## Pregunta experimental

**¿Cómo afecta el valor de `infectiousness` la duración de la epidemia y la cantidad promedio de tortugas enfermas en el modelo Virus de NetLogo?**

---

## Herramientas utilizadas

* NetLogo
* BehaviorSpace
* Google Colab
* R
* tidyverse
* ggplot2
* GitHub Raw
* Overleaf / LaTeX

---

---

## Diseño experimental

Se realizaron dos experimentos en BehaviorSpace:

### 1. Experimento final

Este experimento mide el resultado al final de cada corrida.

| Elemento                | Valor                                   |
| ----------------------- | --------------------------------------- |
| Modelo                  | Virus.nlogox                            |
| Parámetro independiente | `infectiousness`                        |
| Valores probados        | 10, 20, 30, 40, 50 y 60                 |
| Métrica final           | `ticks`                                 |
| Repeticiones            | 30 por cada valor de `infectiousness`   |
| Archivo generado        | `modelo_virus_infectiousness_final.csv` |

---

### 2. Experimento evolutivo

Este experimento mide una variable en cada tick de la simulación.

| Elemento                | Valor                                       |
| ----------------------- | ------------------------------------------- |
| Modelo                  | Virus.nlogox                                |
| Parámetro independiente | `infectiousness`                            |
| Valores probados        | 10, 20, 30, 40, 50 y 60                     |
| Métrica temporal        | `count turtles with [sick?]`                |
| Repeticiones            | 10 por cada valor de `infectiousness`       |
| Archivo generado        | `modelo_virus_infectiousness_evolucion.csv` |

---


## Análisis final

El análisis final compara el valor de `infectiousness` con la duración de la epidemia medida en `ticks`.

El procedimiento realizado fue:

1. Cargar la librería `tidyverse`.
2. Leer el archivo CSV final desde GitHub Raw.
3. Inspeccionar columnas con `head()`, `names()` y `glimpse()`.
4. Renombrar columnas con nombres simples.
5. Seleccionar el parámetro `infectiousness` y la métrica final `ticks`.
6. Generar una gráfica de dispersión.
7. Agregar jitter para visualizar mejor las repeticiones.
8. Agregar color por parámetro.
9. Agregar boxplot agrupado por parámetro.
10. Interpretar la gráfica.



## Análisis evolutivo

El análisis evolutivo estudia cómo cambia el número de tortugas enfermas durante la simulación.

La variable temporal analizada fue:

```netlogo
count turtles with [sick?]
```

El procedimiento realizado fue:

1. Leer el archivo CSV evolutivo.
2. Renombrar columnas como `corrida`, `parametro`, `tiempo` y `valor_temporal`.
3. Seleccionar las columnas relevantes.
4. Graficar tiempo contra cantidad de tortugas enfermas.
5. Colorear por parámetro.
6. Agrupar por parámetro y tiempo.
7. Calcular el promedio de tortugas enfermas por grupo.
8. Graficar líneas de evolución temporal.
9. Usar `facet_wrap` para separar los grupos.
10. Interpretar cómo cambia la dinámica del modelo.



## Interpretación general

El análisis permite observar cómo el parámetro `infectiousness` influye en la dinámica de propagación de la enfermedad.

En general, cuando aumenta `infectiousness`, se espera que la enfermedad tenga mayor facilidad para transmitirse entre los agentes. Esto puede reflejarse en:

* Mayor duración de la epidemia.
* Mayor número promedio de tortugas enfermas.
* Curvas de infección más altas o más prolongadas.
* Mayor variabilidad entre corridas.

La variabilidad entre repeticiones se explica porque el modelo es basado en agentes y contiene elementos aleatorios, como la posición inicial, el movimiento y las interacciones entre tortugas.

---

## Resultados esperados

A partir de las gráficas generadas se espera identificar:

* La tendencia general entre `infectiousness` y `ticks`.
* La dispersión de los resultados entre repeticiones.
* Posibles valores atípicos.
* El pico promedio de tortugas enfermas para cada valor del parámetro.
* La duración aproximada de la epidemia para cada escenario.
* La relación entre las reglas locales de contagio y el comportamiento global del modelo.

---

## Limitaciones del experimento

Algunas limitaciones del análisis son:

* Se estudió principalmente un solo parámetro: `infectiousness`.
* La cantidad de repeticiones puede influir en la estabilidad de los promedios.
* Si se usó una condición de parada con límite máximo de ticks, algunas corridas pudieron terminar antes de que la epidemia desapareciera naturalmente.
* El modelo contiene aleatoriedad, por lo que diferentes corridas con los mismos parámetros pueden producir resultados distintos.



## Código principal en R

El análisis fue desarrollado en R usando principalmente:

```r
library(tidyverse)
```

Funciones usadas:

```r
readLines()
read.csv()
transmute()
select()
group_by()
summarise()
ggplot()
geom_point()
geom_jitter()
geom_boxplot()
geom_line()
facet_wrap()
ggsave()
```


## Conclusiones

1. El parámetro `infectiousness` es fundamental para analizar la dinámica de contagio en el modelo Virus de NetLogo.

2. El análisis final permite comparar la duración de la epidemia para diferentes valores del parámetro.

3. El análisis evolutivo permite observar cómo cambia el número de tortugas enfermas durante el tiempo.

4. Las gráficas generadas en R ayudan a interpretar la tendencia general, la variabilidad entre corridas y los posibles valores atípicos.

5. El uso de BehaviorSpace, GitHub Raw y Google Colab permite construir un flujo de trabajo reproducible para analizar datos de simulaciones basadas en agentes.

---


## Referencias

* NetLogo: https://ccl.northwestern.edu/netlogo/
* BehaviorSpace: https://ccl.northwestern.edu/netlogo/docs/behaviorspace.html
* tidyverse: https://www.tidyverse.org/
* ggplot2: https://ggplot2.tidyverse.org/

```
```
