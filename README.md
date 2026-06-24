## Estimación de la producción mensual de gas convencional en Tierra del Fuego y provincias patagónicas

**Realizado por el alumno:** Gonzalo Ortiz
**Docente**: Nicolas Caballero
**Materia:** Aprendizaje Automático

**Link del video presentación:** 

# Estimación de la producción mensual de gas convencional en Tierra del Fuego y Patagonia mediante modelos de regresión

## Descripción general del proyecto

Este proyecto propone aplicar modelos de aprendizaje automático supervisado para estimar la producción mensual de gas convencional en Tierra del Fuego y provincias patagónicas.

El trabajo utiliza datos históricos oficiales de producción de gas y busca analizar si variables temporales, junto con valores de producción de meses anteriores, permiten aproximar la producción de un mes determinado.

El problema se plantea como una tarea de **regresión supervisada**, ya que la variable que se busca estimar es numérica.

## Objetivo del proyecto

Aplicar modelos de aprendizaje automático para estimar la producción mensual de gas convencional en provincias patagónicas a partir de datos históricos oficiales.

## Dataset utilizado

El dataset seleccionado es **Producción gas SESCO más Tight y Shale capítulo IV por provincia**.

Se trata de un archivo en formato **CSV** que contiene información oficial sobre la producción mensual de gas por provincia, tipo de producción y período de tiempo.

La fuente de los datos es el portal **Datos Argentina**, a partir de registros publicados por la **Secretaría de Energía de la Nación**.

Este dataset fue elegido porque es una fuente pública, oficial y de dominio abierto, lo que permite trabajar con datos reales, verificables y adecuados para un proyecto de aprendizaje automático.

## Origen de los datos

Los datos provienen del portal **Datos Argentina**, dentro del conjunto vinculado a la producción de petróleo y gas publicada por la Secretaría de Energía de la Nación.

La descarga del dataset se realizó durante junio de 2026 para su utilización en el proyecto de la materia Aprendizaje Automático.

No se trata de datos recolectados manualmente, sino de registros administrativos oficiales publicados en formato abierto.

## Descripción del dataset original

En la revisión inicial, el dataset completo presenta:

* **Cantidad de instancias:** 7.494 filas.
* **Cantidad de columnas:** 6 columnas.
* **Formato del archivo:** CSV.
* **Unidad de análisis:** registros mensuales de producción de gas por provincia y tipo de producción.
* **Período observado:** desde enero de 2009 hasta abril de 2026.

Cada fila representa un registro de producción para una provincia, un mes determinado y un concepto de producción de gas.

## Columnas del dataset original

| Columna         | Tipo de dato  | Descripción                                                      |
| --------------- | ------------- | ---------------------------------------------------------------- |
| `anio`          | Entero        | Año correspondiente al registro.                                 |
| `mes`           | Entero        | Mes correspondiente al registro.                                 |
| `indice_tiempo` | Fecha / texto | Identificador temporal del registro, compuesto por año y mes.    |
| `provincia`     | Texto         | Provincia a la que corresponde el dato de producción.            |
| `concepto`      | Texto         | Tipo de producción registrada.                                   |
| `cantidad_mm3`  | Decimal       | Cantidad de gas producida, medida en millones de metros cúbicos. |

## Conceptos incluidos en el dataset

El dataset original incluye distintos conceptos de producción de gas:

* Producción convencional
* Shale gas
* Tight gas

Para este proyecto se decidió trabajar únicamente con **producción convencional**, ya que es el concepto que resulta más adecuado para el análisis propuesto y permite construir una serie histórica comparable entre provincias.

## Recorte utilizado para el proyecto

Para adaptar el dataset al problema de aprendizaje automático, se realizó un recorte del conjunto original.

Primero se filtraron las provincias patagónicas:

* Chubut
* Neuquén
* Río Negro
* Santa Cruz
* Tierra del Fuego

Luego se seleccionaron únicamente los registros correspondientes al concepto:

* **Producción convencional**

Con este recorte, el dataset queda compuesto por:

* **1.040 filas**
* **6 columnas originales**

Este resultado surge de considerar cinco provincias patagónicas durante 208 meses registrados.

## Dataset procesado

Después del filtrado inicial, se realizó un proceso de preparación de datos para generar variables útiles para el modelo.

Las principales transformaciones realizadas fueron:

* Conversión de la variable temporal `indice_tiempo` a formato de fecha.
* Ordenamiento de los datos por provincia y período.
* Selección de registros correspondientes a producción convencional.
* Filtrado de provincias patagónicas.
* Revisión de valores faltantes.
* Creación de variables históricas de producción.
* Creación de variables temporales para representar el comportamiento mensual.
* Eliminación de registros iniciales sin datos históricos suficientes para calcular variables de rezago.

Luego de este procesamiento, el dataset final utilizado para el modelado queda compuesto por:

* **1.025 filas**
* **10 columnas**

La reducción de filas se debe a la creación de variables basadas en meses anteriores. Al calcular variables como la producción del mes anterior, la producción de dos meses antes y el promedio de los últimos tres meses, los primeros registros de cada provincia quedan sin información histórica suficiente y deben eliminarse.

## Columnas del dataset procesado

| Columna                      | Tipo de dato       | Descripción                                                              |
| ---------------------------- | ------------------ | ------------------------------------------------------------------------ |
| `anio`                       | Entero             | Año del registro.                                                        |
| `mes`                        | Entero             | Mes del registro.                                                        |
| `indice_tiempo`              | Fecha              | Fecha mensual del registro.                                              |
| `provincia`                  | Texto / categórica | Provincia patagónica correspondiente al registro.                        |
| `concepto`                   | Texto / categórica | Tipo de producción. En este proyecto se utiliza producción convencional. |
| `cantidad_mm3`               | Decimal            | Producción mensual de gas. Es la variable objetivo.                      |
| `produccion_mes_anterior`    | Decimal            | Producción registrada en el mes anterior para la misma provincia.        |
| `produccion_dos_meses_antes` | Decimal            | Producción registrada dos meses antes para la misma provincia.           |
| `promedio_3_meses`           | Decimal            | Promedio de producción de los últimos tres meses.                        |
| `variacion_mes_anterior`     | Decimal            | Diferencia entre la producción actual y la producción del mes anterior.  |

## Variable objetivo

La variable objetivo del proyecto es:

* `cantidad_mm3`

Esta variable representa la producción mensual de gas convencional medida en millones de metros cúbicos.

El modelo buscará estimar ese valor a partir de variables temporales, datos provinciales y valores históricos de producción.

## Variables predictoras

Las variables predictoras utilizadas o previstas para el modelo son:

* `anio`
* `mes`
* `provincia`
* `produccion_mes_anterior`
* `produccion_dos_meses_antes`
* `promedio_3_meses`
* `variacion_mes_anterior`

Estas variables permiten incorporar información temporal y antecedentes recientes de producción, que son relevantes para estimar el comportamiento del mes siguiente o de un mes determinado.

## Tipo de problema

El proyecto se plantea como un problema de **regresión supervisada**.

Esto se debe a que la variable objetivo es numérica y continua. El modelo no busca clasificar registros en categorías, sino estimar un valor de producción mensual de gas.

## Modelos previstos

Para abordar el problema se utilizarán modelos supervisados de regresión.

Los modelos previstos son:

* Regresión lineal.
* Árbol de decisión para regresión.
* K vecinos más cercanos para regresión.
* Random Forest Regressor como modelo adicional de comparación.

La regresión lineal funcionará como modelo base. Los modelos de árbol y vecinos permitirán comparar si existen mejoras al utilizar métodos capaces de captar relaciones no lineales o patrones de similitud entre registros.

## Métricas de evaluación

Como se trata de un problema de regresión, se utilizarán métricas orientadas a medir errores en valores numéricos.

Las métricas previstas son:

* **MAE:** error absoluto medio. Permite conocer el error promedio de predicción en la misma unidad de la producción.
* **RMSE:** raíz del error cuadrático medio. Penaliza con mayor fuerza los errores grandes.
* **R2:** coeficiente de determinación. Permite observar qué parte de la variación de la producción logra explicar el modelo.

## Información relevante del dataset

El dataset permite analizar la evolución mensual de la producción convencional de gas en provincias patagónicas.

Esto resulta relevante porque la Patagonia tiene un peso importante dentro de la producción energética argentina. En particular, Tierra del Fuego tiene una relación directa con la producción de gas natural, la Cuenca Austral, la actividad offshore, las regalías provinciales, el empleo y la infraestructura energética.

Sin embargo, el dataset no incluye todos los factores que pueden afectar la producción, como precios, inversiones, mantenimiento de instalaciones, decisiones empresariales, entrada de nuevos pozos o cambios regulatorios.

Por ese motivo, el modelo no busca explicar completamente el comportamiento del sector gasífero, sino estimar la producción mensual a partir de los datos históricos disponibles.

## Preprocesamiento realizado

El preprocesamiento aplicado al dataset incluyó los siguientes pasos:

1. Carga del archivo CSV original.
2. Revisión de la cantidad de filas y columnas.
3. Identificación de las variables disponibles.
4. Filtrado de las provincias patagónicas.
5. Selección del concepto producción convencional.
6. Ordenamiento de los registros por provincia y fecha.
7. Conversión de la columna temporal a formato de fecha.
8. Creación de variables predictoras basadas en meses anteriores.
9. Revisión de valores faltantes generados por las variables históricas.
10. Eliminación de registros sin información suficiente para el entrenamiento.
11. Preparación del dataset final para aplicar modelos de regresión.

## División de los datos

Para el entrenamiento y evaluación del modelo se prevé separar los datos en conjuntos de entrenamiento y prueba.

Dado que se trabaja con datos temporales, la división no debe realizarse de forma aleatoria, sino respetando el orden cronológico de los registros.

De esta manera, los datos más antiguos se utilizarán para entrenar el modelo y los datos más recientes para evaluar su desempeño.

## Resultados esperados

Se espera que los modelos puedan captar parte del comportamiento histórico de la producción mensual de gas convencional, especialmente a partir de la producción de meses anteriores y de variables temporales como año y mes.

También es posible que existan limitaciones para anticipar cambios bruscos, ya que la producción de hidrocarburos puede verse afectada por factores externos que no están incluidos en el dataset.

Por lo tanto, los resultados deberán interpretarse como una estimación basada en información histórica y no como una explicación completa del comportamiento del sector energético.

## Estructura sugerida del proyecto

```text
proyecto_gas/
│
├── data/
│   ├── raw/
│   │   └── produccin-gas-sesco-tight-y-shale-captulo-iv-por-provincia.csv
│   └── processed/
│       └── /produccin-gas-sesco-tight-y-shale-captulo-iv-por-provincia.csv
│
├──models:
      ├──modelo_arbol_decision.joblid
│     ├──modelo_regresion_lineal.joblid
│
├──notebooks/
│   └── parcial_producciongas.ipynb
│
├── reports/
│   └── informe_final_produccion_gas.md
│
reports
│     └── informe_final_produccion_gas.md
│
│
└── README.md
```

## Referencias

* Datos Argentina. Producción gas SESCO más Tight y Shale capítulo IV por provincia.
* Secretaría de Energía de la Nación. Producción de Petróleo y Gas.
* Programa de la materia Aprendizaje Automático 2026.


## Referencias

* Datos Argentina. Producción de Petróleo y Gas SESCO.
* Secretaría de Energía de la Nación.
* Material bibliografico y Programa de la materia Aprendizaje Automático 2026.
