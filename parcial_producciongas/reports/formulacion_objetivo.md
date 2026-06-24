“Estimación de la producción mensual de gas convencional en Tierra del Fuego y Patagonia mediante modelos de regresión”

(Corresponde a la entrega 2: Descripción del dataset)
____________________________________

## Dataset seleccionado

Para este proyecto se utilizará el dataset **Producción gas SESCO más Tight y Shale capítulo IV por provincia**, publicado en el portal **Datos Argentina** y proveniente de registros oficiales de la **Secretaría de Energía de la Nación**.

El archivo se encuentra en formato **CSV** y contiene información histórica sobre la producción mensual de gas por provincia, tipo de producción y período de tiempo.

La elección de este dataset responde a que se trata de una fuente pública, oficial y de dominio abierto, lo que permite trabajar con datos reales y verificables para un proyecto de aprendizaje automático.

## Origen de los datos

Los datos provienen del portal **Datos Argentina**, dentro del conjunto de datos vinculado a la producción de petróleo y gas publicada por la Secretaría de Energía de la Nación.

La descarga del dataset se realizó durante junio de 2026 para su uso en el proyecto de Aprendizaje Automático.

No se trata de datos recolectados de forma manual, sino de registros administrativos oficiales publicados en formato abierto. Para este trabajo se realizó un proceso de selección y preprocesamiento con el objetivo de adaptar el dataset al problema de predicción planteado.

## Descripción general del dataset original

En la revisión inicial, el dataset completo presenta:

* **Cantidad de instancias:** 7.494 filas.
* **Cantidad de columnas:** 6 columnas.
* **Formato del archivo:** CSV.
* **Unidad de análisis:** registros mensuales de producción de gas por provincia y tipo de concepto.
* **Período observado:** desde enero de 2009 hasta abril de 2026.

Cada fila representa un registro de producción para una provincia, un mes determinado y un tipo de producción de gas.

## Columnas del dataset original

| Columna         | Tipo de dato aproximado | Descripción                                                                              |
| --------------- | ----------------------- | ---------------------------------------------------------------------------------------- |
| `anio`          | Entero                  | Año correspondiente al registro de producción.                                           |
| `mes`           | Entero                  | Mes correspondiente al registro de producción.                                           |
| `indice_tiempo` | Fecha / texto           | Identificador temporal del registro, compuesto por año y mes.                            |
| `provincia`     | Texto                   | Provincia a la que corresponde el dato de producción.                                    |
| `concepto`      | Texto                   | Tipo de producción registrada. Puede ser producción convencional, shale gas o tight gas. |
| `cantidad_mm3`  | Decimal                 | Cantidad de gas producida, medida en millones de metros cúbicos.                         |

## Variable objetivo

La variable objetivo del proyecto será:

* `cantidad_mm3`

Esta variable representa la producción mensual de gas medida en millones de metros cúbicos.

El objetivo del modelo será estimar ese valor a partir de variables temporales, provinciales y valores históricos de producción.

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

Este resultado surge de considerar 5 provincias patagónicas durante 208 meses registrados.

## Dataset procesado

Luego del filtrado inicial, se realizó un proceso de preparación de datos para generar variables útiles para el modelo.

Las principales transformaciones realizadas fueron:

* Conversión de la variable temporal `indice_tiempo` a formato de fecha.
* Ordenamiento de los datos por provincia y período.
* Selección de registros correspondientes a producción convencional.
* Filtrado de provincias patagónicas.
* Revisión de valores faltantes.
* Creación de variables históricas de producción.
* Creación de variables temporales para representar el comportamiento mensual.
* Eliminación de registros iniciales sin datos históricos suficientes para calcular variables de rezago.

Después de este procesamiento, el dataset final utilizado para modelar queda compuesto por:

* **1.025 filas**
* **10 columnas**

La reducción de filas se debe a la creación de variables basadas en meses anteriores. Al calcular variables como la producción del mes anterior, la producción de dos meses antes y el promedio de los últimos tres meses, los primeros registros de cada provincia quedan sin información histórica suficiente y deben ser eliminados.

## Columnas del dataset procesado

| Columna                      | Tipo de dato aproximado | Descripción                                                              |
| ---------------------------- | ----------------------- | ------------------------------------------------------------------------ |
| `anio`                       | Entero                  | Año del registro.                                                        |
| `mes`                        | Entero                  | Mes del registro.                                                        |
| `indice_tiempo`              | Fecha                   | Fecha mensual del registro.                                              |
| `provincia`                  | Texto / categórica      | Provincia patagónica correspondiente al registro.                        |
| `concepto`                   | Texto / categórica      | Tipo de producción. En este proyecto se utiliza producción convencional. |
| `cantidad_mm3`               | Decimal                 | Producción mensual de gas. Es la variable objetivo.                      |
| `produccion_mes_anterior`    | Decimal                 | Producción registrada en el mes anterior para la misma provincia.        |
| `produccion_dos_meses_antes` | Decimal                 | Producción registrada dos meses antes para la misma provincia.           |
| `promedio_3_meses`           | Decimal                 | Promedio de producción de los últimos tres meses.                        |
| `variacion_mes_anterior`     | Decimal                 | Diferencia entre la producción actual y la producción del mes anterior.  |

## Información relevante del dataset

El dataset permite analizar la evolución mensual de la producción convencional de gas en las provincias patagónicas. Esto es importante porque la Patagonia tiene un peso relevante dentro de la producción energética del país.

En el caso de Tierra del Fuego, el gas convencional tiene especial importancia por su relación con la Cuenca Austral, la producción offshore, las regalías provinciales, el empleo y la infraestructura energética.

El dataset no incluye todos los factores que pueden afectar la producción, como inversiones, precios, mantenimiento de instalaciones, decisiones empresariales, entrada de nuevos pozos o cambios regulatorios. Por ese motivo, el modelo no buscará explicar completamente el comportamiento del sector gasífero, sino estimar la producción mensual a partir de datos históricos disponibles.

## Preprocesamiento realizado

El preprocesamiento realizado sobre los datos incluyó los siguientes pasos:

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

## Tipo de problema

El trabajo se plantea como un problema de **regresión supervisada**, porque la variable objetivo es numérica.

El modelo buscará estimar la producción mensual de gas convencional, medida en millones de metros cúbicos. No se trata de un problema de clasificación, ya que no se busca asignar categorías, sino predecir un valor continuo.

## Conclusión de la entrega

En esta segunda entrega se logró identificar, descargar y describir el dataset que será utilizado en el proyecto de Aprendizaje Automático.

El conjunto de datos seleccionado proviene de una fuente pública y oficial, cuenta con información histórica suficiente y permite construir un problema de regresión supervisada vinculado con la producción mensual de gas convencional en Tierra del Fuego y provincias patagónicas.

A partir del dataset original se realizó un recorte y un preprocesamiento inicial para obtener un conjunto de datos adecuado para la etapa posterior de modelado.
