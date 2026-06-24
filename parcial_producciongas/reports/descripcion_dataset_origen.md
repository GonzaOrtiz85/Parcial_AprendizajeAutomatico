# Estimación de la producción mensual de gas convencional en Tierra del Fuego y provincias patagónicas

## Entrega 1: Descripción y formulación del objetivo

### Descripción del proyecto

Este proyecto propone aplicar modelos de Aprendizaje Automático supervisado para estimar la producción mensual de gas convencional en Tierra del Fuego y otras provincias patagónicas productoras.

La idea central es trabajar con datos históricos oficiales de producción hidrocarburífera y analizar si variables temporales, provinciales y valores de producción de meses anteriores pueden servir para aproximar la producción de un mes determinado.

El trabajo se enfoca en la producción convencional de gas. En el caso de Tierra del Fuego, esta actividad tiene relevancia por su vínculo con la Cuenca Austral, la producción offshore, las regalías provinciales, el empleo, la infraestructura energética y el abastecimiento de gas natural dentro de la matriz energética nacional.

### Contexto del problema

Tierra del Fuego tiene una relación histórica con la producción de hidrocarburos. Dentro de esa actividad, el gas natural ocupa un lugar importante por la presencia de áreas de producción ubicadas tanto en tierra como costa afuera.

La producción de gas forma parte de una cadena productiva más amplia. Primero se encuentra la etapa de exploración y producción, donde las empresas operadoras extraen el recurso. Luego aparece el tratamiento del gas en plantas ubicadas principalmente en la zona norte de la isla y finalmente su transporte hacia el sistema nacional, mediante infraestructura conectada al Gasoducto San Martín.

En Tierra del Fuego conviven operaciones onshore y offshore. Las primeras se desarrollan en tierra, mientras que las segundas se realizan costa afuera. Esta característica le da a la producción gasífera fueguina una dimensión técnica, logística y económica importante.

El problema resulta relevante porque permite aplicar Aprendizaje Automático a un tema vinculado con la producción energética regional. Además, se trabaja con datos reales, públicos y oficiales, lo que permite evitar una variable objetivo artificial. La producción mensual de gas convencional es un dato registrado, medible y comparable en el tiempo.

Desde el punto de vista del Aprendizaje Automático, la producción mensual de gas convencional puede analizarse como una variable numérica observada a lo largo del tiempo. Por ese motivo, el problema se formula como una tarea de regresión.

### Problema que se abordará

El problema que se abordará es la estimación de la producción mensual de gas convencional a partir del comportamiento histórico de la serie de producción.

La pregunta orientadora del proyecto es:

**¿Es posible estimar la producción mensual de gas convencional en Tierra del Fuego y provincias patagónicas utilizando variables temporales, provinciales y valores históricos de producción?**

### Tipo de problema

El proyecto se plantea como un problema de **regresión supervisada**, porque la variable objetivo es numérica.

El valor que se buscará estimar será la producción mensual de gas convencional, medida en millones de metros cúbicos.

No se trata de un problema de clasificación, ya que el objetivo no es asignar categorías, sino predecir un valor continuo de producción.

### Variable objetivo

La variable objetivo será:

`cantidad_mm3`

Esta columna representa la producción mensual de gas medida en millones de metros cúbicos.

El modelo intentará estimar esta variable a partir de información temporal, provincial y de valores históricos de producción.

### Variables predictoras posibles

Las variables predictoras estarán relacionadas con el comportamiento temporal y territorial de la producción. Entre ellas se podrán utilizar:

* Año.
* Mes.
* Provincia.
* Producción del mes anterior.
* Producción de dos meses anteriores.
* Promedio de producción de los últimos tres meses.
* Variación respecto de meses anteriores.

Estas variables podrán ajustarse durante la etapa de preprocesamiento, según la calidad de los datos y los resultados del análisis exploratorio.

### Objetivo general

Aplicar modelos de Aprendizaje Automático supervisado para estimar la producción mensual de gas convencional en Tierra del Fuego y provincias patagónicas a partir de datos históricos oficiales de producción.

### Objetivos específicos

* Describir el contexto productivo del gas natural en Tierra del Fuego y provincias patagónicas.
* Identificar una fuente oficial de datos sobre producción de gas.
* Filtrar y preparar los registros correspondientes a producción convencional de gas.
* Realizar un análisis exploratorio del dataset mediante medidas descriptivas y gráficos.
* Preparar el dataset mediante limpieza, selección de variables y creación de variables temporales e históricas.
* Entrenar modelos de regresión utilizando Python y scikit-learn.
* Evaluar los modelos mediante métricas de regresión como MAE, RMSE y R2.
* Comparar los resultados obtenidos entre los modelos utilizados.
* Elaborar conclusiones sobre el desempeño de los modelos y sus principales limitaciones.

### Modelos posibles

Para abordar el problema se podrán utilizar modelos supervisados de regresión vistos o relacionados con los contenidos de la materia.

**Regresión lineal**

Será utilizada como modelo base. Permitirá observar si las variables temporales e históricas permiten aproximar la producción mensual de gas convencional.

**K vecinos más cercanos para regresión**

Este modelo permitirá estimar valores a partir de registros con características similares. Se relaciona con el contenido de KNN trabajado en la materia.

**Árbol de decisión para regresión**

Este modelo permitirá construir reglas de decisión y captar relaciones que no necesariamente sean lineales.

**Random Forest Regressor**

De manera opcional, se podrá incorporar un modelo de ensamble como comparación adicional. No será el modelo principal, sino una referencia para observar si mejora los resultados respecto de modelos más simples.

### Métricas de evaluación previstas

Al tratarse de un problema de regresión, se utilizarán métricas adecuadas para evaluar errores en valores numéricos.

**MAE**

El error absoluto medio permite conocer el error promedio de predicción en la misma unidad de la producción.

**RMSE**

La raíz del error cuadrático medio penaliza más los errores grandes, por lo que permite observar si el modelo comete errores importantes en algunos meses.

**R2**

El coeficiente de determinación permite observar qué parte de la variación de la producción logra explicar el modelo.

### Resultados esperados

Se espera que los modelos puedan captar parte del comportamiento histórico de la producción mensual de gas convencional, especialmente a partir de la producción de meses anteriores y de variables temporales como mes y año.

El modelo no buscará explicar completamente el comportamiento del sector gasífero, ya que el dataset no incluye todos los factores que pueden afectar la producción, como precios, inversiones, mantenimiento de instalaciones, decisiones empresariales, entrada de nuevos pozos o cambios regulatorios.

---

## Entrega 2: Descripción del dataset

### Dataset seleccionado

Para este proyecto se utilizará el dataset **Producción gas SESCO más Tight y Shale capítulo IV por provincia**, publicado en el portal **Datos Argentina** y proveniente de registros oficiales de la Secretaría de Energía de la Nación.

El archivo se encuentra en formato CSV y contiene información histórica sobre la producción mensual de gas por provincia, tipo de producción y período de tiempo.

La elección de este dataset responde a que se trata de una fuente pública, oficial y de dominio abierto, lo que permite trabajar con datos reales y verificables para un proyecto de Aprendizaje Automático.

### Origen de los datos

Los datos provienen del portal Datos Argentina, dentro del conjunto de datos vinculado a la producción de petróleo y gas publicada por la Secretaría de Energía de la Nación.

La descarga del dataset se realizó durante junio de 2026 para su uso en el proyecto de Aprendizaje Automático.

No se trata de datos recolectados de forma manual, sino de registros administrativos oficiales publicados en formato abierto. Para este trabajo se realizó un proceso de selección y preprocesamiento con el objetivo de adaptar el dataset al problema de predicción planteado.

### Descripción general del dataset original

En la revisión inicial, el dataset completo presenta:

* Cantidad de instancias: 7.494 filas.
* Cantidad de columnas: 6 columnas.
* Formato del archivo: CSV.
* Unidad de análisis: registros mensuales de producción de gas por provincia y tipo de producción.
* Período observado: desde enero de 2009 hasta abril de 2026.

Cada fila representa un registro de producción para una provincia, un mes determinado y un tipo de producción de gas.

### Columnas del dataset original

| Columna         | Tipo de dato aproximado | Descripción                                                                              |
| --------------- | ----------------------- | ---------------------------------------------------------------------------------------- |
| `anio`          | Entero                  | Año correspondiente al registro de producción.                                           |
| `mes`           | Entero                  | Mes correspondiente al registro de producción.                                           |
| `indice_tiempo` | Fecha / texto           | Identificador temporal del registro, compuesto por año y mes.                            |
| `provincia`     | Texto                   | Provincia a la que corresponde el dato de producción.                                    |
| `concepto`      | Texto                   | Tipo de producción registrada. Puede ser producción convencional, shale gas o tight gas. |
| `cantidad_mm3`  | Decimal                 | Cantidad de gas producida, medida en millones de metros cúbicos.                         |

### Recorte utilizado para el proyecto

Para adaptar el dataset al problema de Aprendizaje Automático, se realizó un recorte del conjunto original.

Primero se seleccionaron las provincias patagónicas productoras incluidas en el análisis:

* Chubut.
* Neuquén.
* Río Negro.
* Santa Cruz.
* Tierra del Fuego.

Luego se seleccionaron únicamente los registros correspondientes al concepto:

**Producción convencional**

Con este recorte, el dataset queda compuesto por:

* 1.040 filas.
* 6 columnas originales.

Este resultado surge de considerar 5 provincias patagónicas durante 208 meses registrados.

### Dataset procesado

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

* 1.025 filas.
* 10 columnas.

La reducción de filas se debe a la creación de variables basadas en meses anteriores. Al calcular variables como la producción del mes anterior, la producción de dos meses antes y el promedio de los últimos tres meses, los primeros registros de cada provincia quedan sin información histórica suficiente y deben ser eliminados.

### Columnas del dataset procesado

| Columna                      | Tipo de dato aproximado | Descripción                                                              |
| ---------------------------- | ----------------------- | ------------------------------------------------------------------------ |
| `anio`                       | Entero                  | Año del registro.                                                        |
| `mes`                        | Entero                  | Mes del registro.                                                        |
| `indice_tiempo`              | Fecha / texto           | Identificador temporal del registro.                                     |
| `provincia`                  | Texto / categórica      | Provincia patagónica correspondiente al registro.                        |
| `concepto`                   | Texto / categórica      | Tipo de producción. En este proyecto se utiliza producción convencional. |
| `cantidad_mm3`               | Decimal                 | Producción mensual de gas. Es la variable objetivo.                      |
| `produccion_mes_anterior`    | Decimal                 | Producción registrada en el mes anterior para la misma provincia.        |
| `produccion_dos_meses_antes` | Decimal                 | Producción registrada dos meses antes para la misma provincia.           |
| `promedio_3_meses`           | Decimal                 | Promedio de producción de los tres meses anteriores.                     |
| `variacion_mes_anterior`     | Decimal                 | Variación de producción entre meses anteriores.                          |

### Información relevante del dataset

El dataset permite analizar la evolución mensual de la producción convencional de gas en provincias patagónicas. Esto es importante porque la Patagonia tiene un peso relevante dentro de la producción energética del país.

En el caso de Tierra del Fuego, el gas convencional tiene especial importancia por su relación con la Cuenca Austral, la producción offshore, las regalías provinciales, el empleo y la infraestructura energética.

Sin embargo, el dataset no incluye todos los factores que pueden afectar la producción, como inversiones, precios, mantenimiento de instalaciones, decisiones empresariales, entrada de nuevos pozos o cambios regulatorios. Por ese motivo, el modelo no buscará explicar completamente el comportamiento del sector gasífero, sino estimar la producción mensual a partir de datos históricos disponibles.

### Preprocesamiento realizado

El preprocesamiento realizado sobre los datos incluyó los siguientes pasos:

* Carga del archivo CSV original.
* Revisión de la cantidad de filas y columnas.
* Identificación de las variables disponibles.
* Filtrado de las provincias patagónicas.
* Selección del concepto producción convencional.
* Ordenamiento de los registros por provincia y fecha.
* Conversión de la columna temporal a formato de fecha.
* Creación de variables predictoras basadas en meses anteriores.
* Revisión de valores faltantes generados por las variables históricas.
* Eliminación de registros sin información suficiente para el entrenamiento.
* Preparación del dataset final para aplicar modelos de regresión.

### Tipo de problema asociado al dataset

El trabajo se plantea como un problema de regresión supervisada, porque la variable objetivo es numérica.

El modelo buscará estimar la producción mensual de gas convencional, medida en millones de metros cúbicos. No se trata de un problema de clasificación, ya que no se busca asignar categorías, sino predecir un valor continuo.

### Conclusión de la entrega

En esta segunda entrega se logró identificar, descargar y describir el dataset que será utilizado en el proyecto de Aprendizaje Automático.

El conjunto de datos seleccionado proviene de una fuente pública y oficial, cuenta con información histórica suficiente y permite construir un problema de regresión supervisada vinculado con la producción mensual de gas convencional en Tierra del Fuego y provincias patagónicas.

A partir del dataset original se realizó un recorte y un preprocesamiento inicial para obtener un conjunto de datos adecuado para la etapa posterior de modelado.

