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
